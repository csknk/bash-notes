Find and Replace
================

```bash
find /var/www/html -type f -name .htaccess -exec sed -i 's/1.2.3.4/5.6.7.8/' {} \;
```
