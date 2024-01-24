###                                       UPLOAD FILES IN PHP

To upload a file we will be using a form of method "post" having enctype="multipart/form-data".

<form method="post" enctype="multipart/form-data">
    <input type="file" name="file" id="file" />       
    <!-- here the name atribiute is very important because whatever we had passed in the name attribute is the one through which we fetch the image -->
    <button type="submit" > Submit </button>
</form>

to accept it, we can use `$_POST['img']` 
It contains all the data about any image which is being uploaded,
like:
a) name
b) path
c) file type
d) error

The last details is `error` as we also can see.
    if this property contains value 0 it defines file is uploaded successfully.
    if it contains any value other than 0, it defines there might exist some error whileuploading it.
( can know more about the errors based on the error numbers. ex: 4 defines that the file is not uploaded )

{{

    if ($_SERVER["REQUEST_METHOD"] == "POST") {

    var_dump($_FILES);

    try {

        if (empty($_FILES)) {
            throw new Exception('Invalid upload');
        }

        switch ($_FILES['file']['error']) {
            case UPLOAD_ERR_OK:
                break;

            case UPLOAD_ERR_NO_FILE:
                throw new Exception('No file uploaded');
                break;

            case UPLOAD_ERR_INI_SIZE:
                throw new Exception('File is too large (from the server settings)');
                break;

            default:
                throw new Exception('An error occurred');
        }




        // Restrict the file size: must be less than 1MB
        if ($_FILES['file']['size'] > 1000000) {

            throw new Exception('File is too large');

        }




        // Restrict the file type
        $mime_types = ['image/gif', 'image/png', 'image/jpeg'];

        $finfo = finfo_open(FILEINFO_MIME_TYPE);
        $mime_type = finfo_file($finfo, $_FILES['file']['tmp_name']);

        if ( ! in_array($mime_type, $mime_types)) {
            throw new Exception('Invalid file type');
        }


        // KEEP SAFE OUR FILENAME WITH SOME DANGEROUS CHARACTERS LIKE ( $, !, @, $, %, & etc);s
        $pathinfo = pathinfo($_FILES['file']['name']);

        $base = $pathinfo['filename'];

        $base = preg_replace('/[^a-zA-Z0-9_-]/', '_', $base );

        $filename = $base . "." . $pathinfo['extension']; 
        $destination = "../uploads/$filename" ;


        // What if two users save thier file with the same name, if so we add a counter suffix followed by a '-'.
        // we keep checking if such type of file_exists in our folder using help of a fxn : file_exists('filename');
        $counter = 1; 
        while( file_exists($destination) )
        {
            $filename = $base . "-{$counter}" "." . $pathinfo['extension']; 
            $destination = "../uploads/$filename" ;

            $counter++;
        }



        // move_uploaded_file() isspecificaly used to put the file in the correct destination.
        if (move_uploaded_file($_FILES['file']['tmp_name'], $destination)) {
            echo "File uploaded successfully.";
            
        } else {
            throw new Exception('Unable to move uploaded file');
        }


    } catch (Exception $e) {
        echo $e->getMessage();
    }
}

}}


# unlink($path) Function is used to delete an existing file from the file system.
-> just pass the path inside the parameter and will return true if value is successfully deleted, else return false;

