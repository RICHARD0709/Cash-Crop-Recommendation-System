Cash Crop Recommendation System using Machine Learning
________________________________________
🧠 Project Objective
To help farmers and agricultural stakeholders choose the most suitable crop for cultivation based on soil and climate conditions using a Machine Learning model deployed as a web application.
________________________________________
🏗️ Tech Stack Overview
Layer	Technologies Used
Frontend	HTML, CSS (via index.html), Jinja2 Templates
Backend	Python, Flask (Web Framework)
Machine Learning	Scikit-learn, NumPy, Pickle
Model Deployment	Flask server with pre-trained .pkl model and scalers
________________________________________
🌐 Frontend (User Interface)
•	File: index.html
•	Built with: HTML + embedded Jinja2 templating syntax.
•	Purpose:
o	Presents a form with inputs for:
	Nitrogen
	Phosphorus
	Potassium
	Temperature
	Humidity
	pH
	Rainfall
o	Displays prediction result dynamically after form submission.
✅ User Experience: Simple, clean UI allowing users (especially farmers or agricultural officers) to input soil data and instantly get crop recommendations.
________________________________________
🧩 Backend (Application Logic with Flask)
•	File: app.py
•	Framework: Flask (lightweight Python web framework)
•	Roles of Flask in the Project:
o	Acts as a web server and controller.
o	Handles routing:
	'/' → shows the input form (index page).
	'/predict' → accepts form input (POST), makes prediction, and returns result.
o	Interacts with the ML model and data scalers to preprocess input and generate prediction.
________________________________________
🔢 ML Model and Data Preprocessing
•	Models & scalers saved as .pkl files using pickle:
o	model.pkl → Trained classification model (like Random Forest, SVM, etc.).
o	minmaxscaler.pkl → Used to normalize input features between 0 and 1.
o	standscaler.pkl → Standardizes input features (mean = 0, std = 1).
🔄 Prediction Pipeline Flow:
1.	Form input collected via POST request.
2.	Input reshaped into NumPy array and scaled:
o	First by MinMaxScaler
o	Then by StandardScaler
3.	Preprocessed data is passed to model.predict().
4.	The predicted class (e.g., 4) is mapped to a crop using a dictionary (e.g., 4 = Cotton).
5.	Result is returned and displayed in the browser.
Model Output
•	A class label (1 to 22), each corresponding to a specific crop:
o	e.g., 1 = Rice, 5 = Coconut, 13 = Banana, etc.
•	The final output is:
"Banana is the best crop to be cultivated right there"
