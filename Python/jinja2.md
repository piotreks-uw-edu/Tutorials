# Jinja2 is a modern and designer-friendly templating engine for the Python programming language. #
# It is used primarily to produce dynamic web content, where you can use it to insert values into HTML, XML, or other markup formats.  #

# base.jinja2 #
<html>
<head>
<title>Calculator</title>
</head>
<body>
    <h1>Calculator</h1>
    <h2>{% block subtitle %} {% endblock subtitle %}</h2>
    {% block content %} {% endblock content %}
</body>

</html>

# add.jinja2 #
{% extends 'base.jinja2' %}

{% block subtitle %}Add them up!{% endblock subtitle %}

{% block content %}
    <p>Total: <span id="total">FILL ME</span></p>
    <form method="POST">
        <label for="number">Number: </label><input type="number" id="number" nam="number">
        <input type="submit" value="Add It!"
    </form>
{% endblock content %}


