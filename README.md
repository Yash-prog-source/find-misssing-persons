Find Missing Person using AI
Issues Stars

Web App Version of this Project
Youtube Link
Hundreds of people (especially children go missing every day) in India. There are various NGO's and Govt Initiatives to help with it. This project tries to implement an existing/new way to help.

List of contents
News Articles
Objective
Solution
Installation
What is left/not working?
News Articles
Article 1
News Article 1

Article 2
News Article 2

What is the objective of this Project and how will it help?
The objective of this project is to help Police and higher authorities to track down missing people quickly. The usual process to track a person is using investigation which requires time and experience (to ask right questions). Most of the time, investigation method works pretty well but it is time consuming and can be unsuccessful if the person (missing) has been shifted/moved to different location (city/country).
In such cases, the ideal approach is to go through CCTV footages and evidences. Again, this can be very time consuming and given the number of people that go missing everyday, it can be a challanage to keep up with it.

Solution (Project's Implementation)
1. Registering New Cases
The first step is to register a new case. The GUI application is built using PyQT5 that allows you to collect all relevant information and store it in database Postgres.

Please ignore the SRK's image. It is just for the sake of project :)

New Case Window

2. Waiting for Users to submit images
So far we have only talked about 'how new cases will be registered', the next thing we have to do is to match these registered cases but who do we match it with? This is where ours Users come in. These users are common people like you and me who wants to make a change in the society.
The common people will use an application on their mobile to submit photos of people who they think have lost or found begging while keeping them their identity anonymous. The anonymous part is very important because they fear of local Gundas that might create trouble for them.

Mobile Application Mobile Application

An android Application can also be build and used but I have very little experience in it.

3. Matching Cases
The next step is to match the case images and user submitted images. To match KNN Algorithm is used. Main Application

How to run
1. With Docker (Easy)
Prerequisites

Docker (docker-compose as well)
$ git clone https://github.com/gaganmanku96/Finding-missing-person-using-AI
$ cd Finding-missing-person-using-AI
$ docker-compose up --build
$ cd app
$ pip install -r requirements.txt --no-cache-dir
$ python login_window.py
At this point you'll see a window like this Login Window

Default username: admin Default password: admin

Login window makes sure that only authenticated can view the registered cases. Each user can only view the cases submitted by him. NOTE: There is no concpet of superuser.

After logging in you'll see the main screen through which you'll be able to submit cases.

To run the mobile application:
$ cd mobile_app
or (if you are inside app dir)

$ ../mobile_app
$ python ui.py
After that you'll see a window like this
mobile application

You can this to submit user images or you can create your own mobile app.

Once done you'll have to Click on Refresh button on train KNN Model and then on Match to start Matching Images.

2. Without Docker (Intermediate)
Here are the step you have to do

Install Postgres Database and replace the username and password in config/.env.file
The next step is to run database and make sure it is working.
$ cd database
$ pip install -r requirements.txt
$ uvicorn main:app --port 8002
Next, the face encoding api
$ cd face_encoding
$ pip install -r requirements.txt
$ uvicorn main:app --port 8000
If you are using non-conda environment like venv then it might give error while installing dlib library.

Running the application
$ cd app
$ pip install -r requirements.txt
$ python login.py
At this point you'll see a window like this Login Window

Default username: admin Default password: admin

Login window makes sure that only authenticated can view the registered cases. Each user can only view the cases submitted by him. NOTE: There is no concpet of superuser.

After logging in you'll see the main screen through which you'll be able to submit cases.

To run the mobile application:
$ cd mobile_app
or (if you are inside app dir)

$ ../mobile_app
$ python ui.py
After that you'll see a window like this
mobile application

You can this to submit user images or you can create your own mobile app.

Once done you'll have to Click on Refresh button on train KNN Model and then on Match to start Matching Images.

What is left?
 Login (Authentication)
 Submit new case
 Mobile Application (to submit user photos)
 View submitted cases
 View confirmed cases
 Unit tests
