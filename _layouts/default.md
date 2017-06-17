<!DOCTYPE html>
<html lang="en">
<head>
  <title>{% if page.title %}{{ page.title }} – {% endif %}{{ site.name }} – {{ site.description }}</title>

  <!-- jQuery 3 -->
  <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.2.1/jquery.min.js"></script>

  <!-- jQuery Mobile -->
  <script src="https://ajax.googleapis.com/ajax/libs/jquerymobile/1.4.5/jquery.mobile.min.js"></script>
  <link rel="stylesheet" href="https://ajax.googleapis.com/ajax/libs/jquerymobile/1.4.5/jquery.mobile.min.css">

  <!-- jQuery UI -->
  <link rel="stylesheet" href="https://ajax.googleapis.com/ajax/libs/jqueryui/1.12.1/themes/smoothness/jquery-ui.css">
  <script src="https://ajax.googleapis.com/ajax/libs/jqueryui/1.12.1/jquery-ui.min.js"></script>

  <!-- Bootstrap 3.3.7 -->
  <link href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/css/bootstrap.min.css" rel="stylesheet">
  <script src="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/js/bootstrap.min.js"></script>

  <!-- Fonts -->
  <link href="https://fonts.googleapis.com/css?family=Open+Sans" rel="stylesheet">
  <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/font-awesome/4.7.0/css/font-awesome.min.css" />

  <!-- My Styling -->
  <link rel="stylesheet" href="{{ "/static/css/default.css" | relative_url }}">

  <!-- UUDDLRLRBA -->
  <script src="{{ "/static/js/jGravity.js" | relative_url }}"></script>
  <script src="{{ "/static/js/uuddlrlrba.js" | relative_url }}"></script>
</head>
<body>
{% include nav.html %}
<!-- Page Content -->
<div class="container">
  {{content}}
</div>

<!-- including footer -->
{% include footer.html %}

</body>
</html>
