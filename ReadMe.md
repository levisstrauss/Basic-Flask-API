===================== Api creation with Flask ====================


                   ====== Installation =======

1 - Create a new project

2 - create the requirements.txt file

2 - install all dependencies such as: 

3 -  Create the app.py file

       Flask==1.0.3
       httpie==1.0.2

4 - To run these dependencies type in the terminal:

     pip install -r requirements.txt

5 - Set up the app file 

     from flask import Flask
     app = Flask(__name__)
     @app.route("/")
     def hello():
         return "Hello World!"
    if __name__ == "__main__":
         app.run()

=> get all the recipes using GET:
 
    curl -i -X GET localhost:5000/recipes                 or using the browser
    http://localhost:5000/recipes


    Here, you should get all the receipes available 

    Take a look at the response we get. The first few lines in the response are the header. It has the HTTP status 200 OK and a Content-Length of 175 bytes. The Content-Type is application/json and, in the end, we have the response body in JSON format:
      HTTP/1.0 200 OK
      Content-Length: 175
      Content-Type: application/json
      Date: Mon, 15 Jul 2019 12:40:44 GMT
      Server: Werkzeug/0.15.4 Python/3.7.0

=> Create a new recipes using POST:
    
    Using curl
    curl -i -X POST localhost:5000/recipes -H "Content-Type: application/
      json" -d '{"name":"Cheese Pizza", "description":"This is a lovely cheese
      pizza"}'

    Using the broswer

    http POST localhost:5000/recipes name="Cheese Pizza" description="This is
    a lovely cheese pizza"
    If everything is right, you should see the response 

=> Let's update using PUT:
    
      http PUT localhost:5000/recipes/3 name="Lovely Cheese Pizza"
      description="This is a lovely cheese pizza recipe."


     curl -i -X PUT localhost:5000/recipes/3 -H "Content-Type: application/
     json" -d '{"name":"Lovely Cheese Pizza", "description":"This is a lovely
     cheese pizza recipe."}'
    

      HTTP/1.0 200 OK
      Content-Length: 92
      Content-Type: application/json
      Date: Tue, 16 Jul 2019 02:04:57 GMT
      Server: Werkzeug/0.15.4 Python/3.7.0
      {
          "description": "This is a lovely cheese pizza recipe.",
          "id": 3,
          "name": "Lovely Cheese Pizza"
      }

=> Getting a particular recipes based on the provided ID:
   
      curl -i -X GET localhost:5000/recipes/3

      http GET localhost:5000/recipes/3

      if we try with an undefined ID, It will never work


      {
           "message": "recipe not found"
      }

=> Test your basic Api using POSTMAN 

    GET : http://localhost:5000/recipes => Get all the recipes
    GET : http://localhost:5000/recipes/1 => Get a specific recipe id = 1
    POST : http://localhost:5000/recipes => Create a recipe 
    PUT : http://localhost:5000/recipes/1 => Update a recipe  id = 1
    DEL : http://localhost:5000/recipes/1 => Delete a recipe  id = 1
