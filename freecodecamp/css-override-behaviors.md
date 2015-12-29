css override behaviors
========

body->element->class->id->inline style
<htm>
<body>
  <style>
    body {
      background-color: black;
      font-family: Monospace;
      color: green;
    }
    #orange-text {
      color: orange;
    }
    .pink-text {
      color: pink;
    }
    .blue-text {
      color: blue;
    }
  </style>
  <h1 id="orange-text" class="pink-text blue-text" style="color:white">Hello World!</h1>
</body>
</html>
