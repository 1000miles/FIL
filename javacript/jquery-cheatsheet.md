# jQuery Cheat Sheet

**.ready();**
  ```
  $(document).ready(function()){
    ...
  };
  ```

## A-Z

**.addClass();**
  ```
  $(selector).addClass(class);

  Examples:

  $("class").addClass("btn");
  $("type").addClass("btn");

  $(".target:odd").addClass("animated shake");
  $(".target:even").addClass("animated shake");
  $(".target:nth-child(2)").addClass("animated bounce");

  $("body").addClass("animated fadeOut");
  $("body").addClass("animated hinge");
  ```

**.animate();**
  ```
  $(selector).animate({property: value});

  Examples:

  $("div").animate({left: '250px'});
  ```

**.appendTo();**
  ```
  $(selector).appendTo(element);

  Examples:

  $("#target").appendTo("#left-column");
  ```

**.children();**
  ```
  $(selector).children(property, value);

  Examples:

  $("#left-well").children().css("color", "blue")
  ```

**.click();**
  ```
  $(selector).click();

  Examples:

  $("button").click( function(){
    ...
  });
  ```

**.clone();**
  ```
  $(selector).clone();

  Examples:

  $("#target5").clone().appendTo("#left-well");
  ```

**.css();**
  ```
  $(selector).css(class, value);

  Examples:

  $("#target").css("color", "red");
  ```

**.fadeIn();
.fadeOut();
.fadeToggle();
.fadeTo();**
  ```
  $(selector).fadeIn(speed,callback);

  Examples:

  $("#div1").fadeIn();
  $("#div2").fadeIn("slow");
  $("#div3").fadeIn(3000);
  ```

**.hide()**
  ```
  $(selector).hide();

  Examples:

  $("p").hide()
  $(this).hide()
  ```

**.html();**
  ```
  $(selector).html(html-code);

  Examples:

  $("#target").html("<b>Hello world!</b>");
  ```

**.load();**
  ```
  $(selector).load(URL,data,callback);

  Examples:

  ```

**.parent();**
  ```
  $(selector).parent()

  Examples:

  $("#target").parent().css("background-color", "red");
  ```

**.prop();**
  ```
  $(selector).prop(property, value)

  Examples:

  $("#target").prop("disabled", true);
  ```

**.remove();**
  ```
  $(selector).remove();

  Examples:

  $("#target").remove();
  ```

**.removeClass();**
  ```
  $(selector).removeClass(class);

  Examples:

  $("#target").removeClass("color");
  ```

**.text();**
  ```
  $(selector).text(string);

  Examples:

  $("p").text("Hello world!");
  ```

**.val();**
  ```
  $(selector).val(value);

  Examples:

  $("#target").val("Hello World!");
  ```
