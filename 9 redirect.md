###                             R E D I R E C T   I N    P H P

We can redirect in php using a simple function called `header( Location: url );`
It will accepts a single string parameter like: | "Location: your_url " |.

ex: 

{{
    header("Location: article.php?id=$id");
}}

