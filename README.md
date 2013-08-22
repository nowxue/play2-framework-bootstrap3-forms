Play 2 framework's form helpers for Twitter's Bootstrap 3.0
============================================================

Currently supported:

* Input text
* Textarea
* Checkbox

Usage
------

You can use a FieldConstructor directly by adding this class to your *app/controllers/helpers* folder
(this example is valid for InputText objects):

    package controllers.helpers
    
    import views.html.helper.FieldConstructor
    
    object BootstrapHelper {
      implicit val myFields = FieldConstructor(views.html.helper.bootstrapInput.f)
    }
    
And then, you should import it into your template by:

    @import helpers.BootstrapHelper._

Remember you can't have two implict *FieldConstructors* in a template, so if you have a form with multiple
input types, you can import use one *FieldConstructor*, and overwrite it with explicit parameters:

    @inputText(textForm("title"), 'help -> "Use a short title please")
    @inputText(textForm("introduction"))
    @textarea(textForm("text"), 'help -> "You can use HTML here")(FieldConstructor(views.html.helper.bootstrapTextarea.f), null)
    @checkbox(textForm("visible"))(FieldConstructor(views.html.helper.bootstrapCheckbox.f), null)

As you can see, there's a custom argument defined, named *help*. You can use custom parameters in your helpers by using:

    @elements.args.get('your_argument)

I'll develop different input types as I need them in a project. Feel free to contribute/modify/whatever.

You can find more info about Play 2 form helpers here:

* http://stackoverflow.com/questions/15930343/multiple-fieldconstructor-in-playframework-2-1
* http://www.playframework.com/documentation/2.0/JavaFormHelpers