PROJECT: HackYourTemperature II

    This week you'll continue building on HackYourTemperature. Inside the folder homework, create a new folder called hackyourtemperature.

So far you've build a basic web server. We've loaded in the necessary modules. We have one end point, which is /. And we have activated the server, by listening to a port number.

This week's homework we will expand on that, in 2 parts:

    We'll make templates to create a frontend that will be a simple page with a form
    We'll create a POST route that will allow us to access the submitted form data

4.1 The Frontend

Since we've already loaded in our package express-handlebars, we can get started immediately. If at any point you're stuck, try reading the documentation or ask a question in Slack!

    We first have to make Express aware of the templating engine. We do this by using the engine() and set() functions. Paste in the following (and figure out what it does, by checking the documentation):

app.set('view engine', 'handlebars');
app.engine('handlebars', exphbs({ defaultLayout: false }));

    In the root of the project folder, create a new folder called views.
    Create 1 .handlebars file inside the views folder, named index.handlebars
    The content of main.handlebars should be a regular, complete HTML document. Write a basic structure, including a <head> and <body>. The latter should include a <form>. Make sure it has an <input> field, which should be of type="text" and have a name="cityName". Also add a submit button. The form should be submitted to our POST request endpoint, which is /weather. Let the form know about this endpoint by passing it as a value to the action property: action="/weather"
    Test out your work! Make sure it renders a form in your browser

4.2 The Backend

In this part we'll add another endpoint, with a POST method.

    First let's modify our / route. Instead of sending a string, send a template using the render() function. Pass in the name of the template, which is index
    To make Express aware of what data type the incoming data is (which is JSON). We do that using the json() method on the Express object. Using the use() function from app, pass in the json() from express.
    Create a POST route, that has as an endpoint: /weather
    Inside the callback function of the route, get access to the cityName and put it inside a variable. Hint: use the body object from the request to find it.
    Send the the form input back as a response to the client

Test out your work using Postman and make sure that any time you submit something in the form, it returns as a response from the server the exact words you submitted.