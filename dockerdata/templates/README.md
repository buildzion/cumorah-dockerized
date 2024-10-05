# Template overrides

This directory is inserted into the template search path by
`cumorah.settings.production`. Any template you want to
override can be placed here where it will take precedence over
and replace the default template.

Common templates to consider overriding:
 * base.html
 * cumorah/nav_header.html
 * repository/collection_page.html
 * repository/document_page.html

To customize the login/logout templates you can find their originals
in the python installation site-packages folder under
`allauth/templates/account/*.html`.
