# Integrate Machine Learning into Web Applications with Flask


We all have come across various web applications that use machine learning. For example, Netflix and YouTube use ML to personalize your experience by recommending you new content based on your viewing history. This helps them make better decisions and understand the browsing behaviors of their users.

Even you can create such an application in which you feed your input data and it predicts the output for you using your ML model. The machine learning models that you create can be put to better use if you can integrate your models into an application. This not only highlights your ML knowledge but also your app development skills.

In this article, I will teach you how to embed an ML model in your Web Application with Flask. Firstly, we will create a simple linear regression model to predict the CO2 emission from vehicles. Then we will develop a web application that takes the input to predict the emission.

1. Create your machine learning model
2. Develop your web application with Flask and integrate your model in the app
3. Deploy your web-app in Heroku Cloud Platform



# 1. Create your machine learning model
We use linear regression to predict the CO2 emission from vehicles. The dataset has many columns but we only use a few of them as our features. The last column represents the class label. Our dataset has 1067 rows and 4 columns.

We use the built-in LinearRegression() class from sklearn to build our regression model. The following code helps us save our model using the Pickle module. Our ML model is saved as “model.pkl”. We will later use this file to predict the output when new input data is provided from our web-app.

# 2. Develop your web application with Flask and integrate your model
Now that we have our model, we will start developing our web application with Flask. Those of you starting out in Flask can read about it here.

Flask learning resources: Flask Tutorials by Corey Schafer, Learn Flask for Python — Full Tutorial

## 2.1. Install Flask:
You can use the ‘pip install flask’ command. I use the PyCharm IDE to develop flask applications. To easily install libraries in PyCharm follow these steps.

## 2.2. Import necessary libraries, initialize the flask app, and load our ML model:
We will initialize our app and then load the “model.pkl” file to the app.

## 2.3. Define the app route for the default page of the web-app :
Routes refer to URL patterns of an app (such as myapp.com/home or myapp.com/about). @app.route("/") is a Python decorator that Flask provides to assign URLs in our app to functions easily.


## 2.4. Redirecting the API to predict the CO2 emission :
We create a new app route (‘/predict’) that reads the input from our ‘index.html’ form and on clicking the predict button, outputs the result using render_template.

## 2.5. Starting the Flask Server :
```
if __name__ == "__main__":
    app.run(debug=True)
```    
app.run() is called and the web-application is hosted locally on [localhost:5000].

“debug=True” makes sure that we don’t require to run our app every time we make changes, we can simply refresh our web page to see the changes while the server is still running

# Project Structure
The project is saved in a folder called “heroku_app”. We first run the ‘mlmodel.py’ file to get our ML model and then we run the ‘app.py’. On running this file, our application is hosted on the local server at port 5000.


- FuelConsumption.csv — This is the dataset we used
- mlmodel.py — This is our machine learning code
- model.pkl — This is the file we obtain after we run the mlmodel.py file. It is present in the same directory
- app.py — This is the Flask application we created above
- templates — This folder contains our ‘index.html’ file. This is mandatory in Flask while rendering templates. All HTML files are placed under this folder.
- static — This folder contains the “css” folder. The static folder in Flask application is meant to hold the CSS and JavaScript files.

It is always a good idea to run your application first in the local server and check the functionality of your application before hosting it online in a cloud platform. Let’s see what happens when we run ‘app.py’ :


Now, let’s enter the required values and click on the “Predict” button and see what happens.

Observe the URL (127.0.0.1:5000/predict), this is the use of app routes. On clicking the “Predict” button we are taken to the predict page where the predict function renders the ‘index.html’ page with the output of our application.

# 3. Deploy your Web Application on Heroku
Now that our application has been successfully tested on the local server, it’s time to deploy our application on Heroku- cloud platform. There are two prerequisites to deploy any flask web-app to Heroku.

On the Project Structure, you might have noticed two new files named “Procfile” and “requirements.txt”. These two files are required to deploy your app on Heroku.

Before creating Procfile, we need to install Gunicorn. You can use the command ‘pip install gunicorn’ or use the above link to install libraries in PyCharm

## 3.1. Create Procfile :
A Procfile specifies the commands that are executed by a Heroku app on startup. Open up a new file named Procfile (without any extension) in the working directory and paste the following.
```
web: gunicorn app:app
```
## 3.2. Create requirements.txt: The requirements.txt file will contain all of the dependencies for the flask app. Open a new file and name it as “requirements.txt”. Mention all the requirements as following :
```
Flask==1.1.1
gunicorn==20.0.4
pandas==0.25.2
scikit-learn==0.23.2
numpy==1.17.3
pickle4==0.0.1
sklearn==0.0
```
Alternatively, you can also use the following command in your terminal in the working directory to create this file:
```
pip freeze > requirements.txt
```

## 3.3. Upload all files on your GitHub Repository :
To learn how to create a new repository, click here. You can take help from here if you want to learn how you can upload files to your repository. Your repository should look somewhat like this once all files are uploaded.