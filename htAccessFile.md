To deploy the mixs-as-rdf on the gensc server, we need to handling incoming requests like:

http://gensc.org/ns/mixs/ploidy

and map them to:

http://gensc.org/ns/mixs/index.htm#ploidy

The following is the .htaccess file that is inserted on the gensc server under public\_html/ns/mixs to re-write incoming requests. This piece of code is not inserted into the code repository as this is potentially system specific.

```
Options +FollowSymLinks +SymLinksIfOwnerMatch

<IfModule mod_rewrite.c>
RewriteEngine On
RewriteBase /
RewriteCond %{REQUEST_FILENAME} !-f 
RewriteCond %{REQUEST_FILENAME} !-d 
RewriteCond %{REQUEST_URI} !\.htm$ [NC] 
RewriteCond %{REQUEST_URI}  ^/ns/mixs/([^/]+)/? [NC]
RewriteRule .*       /ns/mixs/index.htm#%1           [R,NE,L]
</IfModule>
```