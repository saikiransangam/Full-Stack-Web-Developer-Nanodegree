# Backend - Full Stack Trivia API

### Installing Dependencies for the Backend

1. **Python 3.7** - Follow instructions to install the latest version of python for your platform in the [python docs](https://docs.python.org/3/using/unix.html#getting-and-installing-the-latest-version-of-python)


2. **Virtual Enviornment** - We recommend working within a virtual environment whenever using Python for projects. This keeps your dependencies for each project separate and organaized. Instructions for setting up a virual enviornment for your platform can be found in the [python docs](https://packaging.python.org/guides/installing-using-pip-and-virtual-environments/)


3. **PIP Dependencies** - Once you have your virtual environment setup and running, install dependencies by naviging to the `/backend` directory and running:
```bash
pip install -r requirements.txt
```
This will install all of the required packages we selected within the `requirements.txt` file.


4. **Key Dependencies**
 - [Flask](http://flask.pocoo.org/)  is a lightweight backend microservices framework. Flask is required to handle requests and responses.

 - [SQLAlchemy](https://www.sqlalchemy.org/) is the Python SQL toolkit and ORM we'll use handle the lightweight sqlite database. You'll primarily work in app.py and can reference models.py.

 - [Flask-CORS](https://flask-cors.readthedocs.io/en/latest/#) is the extension we'll use to handle cross origin requests from our frontend server.

### Database Setup
With Postgres running, restore a database using the trivia.psql file provided. From the backend folder in terminal run:
```bash
psql trivia < trivia.psql
```

### Running the server

From within the `./src` directory first ensure you are working using your created virtual environment.

To run the server, execute:

```bash
flask run --reload
```

The `--reload` flag will detect file changes and restart the server automatically.

## ToDo Tasks
These are the files you'd want to edit in the backend:

1. *./backend/flaskr/`__init__.py`*
2. *./backend/test_flaskr.py*


One note before you delve into your tasks: for each endpoint, you are expected to define the endpoint and response data. The frontend will be a plentiful resource because it is set up to expect certain endpoints and response data formats already. You should feel free to specify endpoints in your own way; if you do so, make sure to update the frontend or you will get some unexpected behavior.

1. Use Flask-CORS to enable cross-domain requests and set response headers.


2. Create an endpoint to handle GET requests for questions, including pagination (every 10 questions). This endpoint should return a list of questions, number of total questions, current category, categories.


3. Create an endpoint to handle GET requests for all available categories.


4. Create an endpoint to DELETE question using a question ID.


5. Create an endpoint to POST a new question, which will require the question and answer text, category, and difficulty score.


6. Create a POST endpoint to get questions based on category.


7. Create a POST endpoint to get questions based on a search term. It should return any questions for whom the search term is a substring of the question.


8. Create a POST endpoint to get questions to play the quiz. This endpoint should take category and previous question parameters and return a random questions within the given category, if provided, and that is not one of the previous questions.


9. Create error handlers for all expected errors including 400, 404, 422 and 500.



## API Reference


## API Reference

### Getting Started
- Base URL: http://127.0.0.1:5000/
- Frontend Base URL: http://127.0.0.1:3000/

### Error Handling
Errors are returned in the following json format:
```
{
    'success': False,
    'error': 404,
    'message': 'Resource not found. Input out of range.'
}
```
The API returns 4 types of errors:
- 400: bad request
- 404: not found
- 422: unprocessable
- 500: internal server error

### Endpoints

##### GET '/categories'
- General:
   - Fetches a dictionary of all available categories.
- Fetches a dictionary of categories in which the keys: ids and value: string of the category
- Example: ```curl http://127.0.0.1:5000/categories```
```
{
  "categories": {
    "1": "Science",
    "2": "Art",
    "3": "Geography",
    "4": "History",
    "5": "Entertainment",
    "6": "Sports"
  },
  "success": true
}
```
##### GET '/questions'
- Fetches all the questions in the database.
- Questions are paginated with 10 questions each page.
- Returns number of questions and number of categories.
- Example: ```curl http://127.0.0.1:5000/questions```
```
{
  "categories": {
    "1": "Science",
    "2": "Art",
    "3": "Geography",
    "4": "History",
    "5": "Entertainment",
    "6": "Sports"
  },
  "questions": [
    {
      "answer": "Maya Angelou",
      "category": 4,
      "difficulty": 2,
      "id": 5,
      "question": "Whose autobiography is entitled 'I Know Why the Caged Bird Sings'?"
    },
    {
      "answer": "Muhammad Ali",
      "category": 4,
      "difficulty": 1,
      "id": 9,
      "question": "What boxer's original name is Cassius Clay?"
    },
    {
      "answer": "Apollo 13",
      "category": 5,
      "difficulty": 4,
      "id": 2,
      "question": "What movie earned Tom Hanks his third straight Oscar nomination, in 1996?"
    },
    {
      "answer": "Tom Cruise",
      "category": 5,
      "difficulty": 4,
      "id": 4,
      "question": "What actor did author Anne Rice first denounce, then praise in the role of her beloved Lestat?"
    },
    {
      "answer": "Edward Scissorhands",
      "category": 5,
      "difficulty": 3,
      "id": 6,
      "question": "What was the title of the 1990 fantasy directed by Tim Burton about a young man with multi-bladed appendages?"
    },
    {
      "answer": "Brazil",
      "category": 6,
      "difficulty": 3,
      "id": 10,
      "question": "Which is the only team to play in every soccer World Cup tournament?"
    },
    {
      "answer": "Uruguay",
      "category": 6,
      "difficulty": 4,
      "id": 11,
      "question": "Which country won the first ever soccer World Cup in 1930?"
    },
    {
      "answer": "George Washington Carver",
      "category": 4,
      "difficulty": 2,
      "id": 12,
      "question": "Who invented Peanut Butter?"
    },
    {
      "answer": "Lake Victoria",
      "category": 3,
      "difficulty": 2,
      "id": 13,
      "question": "What is the largest lake in Africa?"
    },
    {
      "answer": "The Palace of Versailles",
      "category": 3,
      "difficulty": 3,
      "id": 14,
      "question": "In which royal palace would you find the Hall of Mirrors?"
    }
  ],
  "success": true,
  "total_questions": 19
}
```
##### DELETE '/questions/int:id'
- Delete the question by id in the url parameters.
- Example: ```curl -X DELETE http://127.0.0.1:5000/questions/7```
```
{
    "success": "True",
    "deleted": 7
}
```

##### POST '/questions'
- Create a new question.
- Return results with new question with pagination.
- Example: ```curl -X POST - H "Content-Type: application/json" -d '{"question": "Who is Donald Trump?", "answer": "the current president of US", "difficulty": 3, "category": "7"}' http://127.0.0.1:5000/questions```
```
{
  "success": true
  "created": 21
  "total_questions": 21
}
```

##### POST '/questions/search'
- Return searched questions.
- Example: ```curl -X POST -H "Content-Type: application/json" -d '{"searchTerm": "peanut butter"}' http://127.0.0.1:5000/questions/search```

```
{
  "questions": [
    {
      "answer": "George Washington Carver",
      "category": 4,
      "difficulty": 2,
      "id": 12,
      "question": "Who invented Peanut Butter?"
    }
  ],
  "success": true,
  "total_questions": 1
}
```

##### GET '/categories/int:id/questions'
- Gets questions in a specific category
- Example: ```curl http://127.0.0.1:5000/categories/2/questions```

```
{
  "current_category": "Art",
  "questions": [
    {
      "answer": "Escher",
      "category": 2,
      "difficulty": 1,
      "id": 16,
      "question": "Which Dutch graphic artist\u2013initials M C was a creator of optical illusions?"
    },
    {
      "answer": "Mona Lisa",
      "category": 2,
      "difficulty": 3,
      "id": 17,
      "question": "La Giaconda is better known as what?"
    }
  ],
  "success": true,
  "total_questions": 2
}
```

##### POST '/quizzes'
- Users can play the game.
- Return Random questions.
- Example: ```curl -X POST -H "Content-Type: application/json" -d '{"previous_questions": [2, 6], "quiz_category": {"type": "Entertainment", "id": "5"}}' http://127.0.0.1:5000/quizzes```
```
{
  "question": {
    "answer": "Kiran",
    "category": 3,
    "difficulty": 4,
    "id": 4,
    "question": "What actor did author Anne Rice first denounce, then praise in the role of her beloved Lestat?"
  },
  "success": true
}
```
## Author
- Sai Kiran Sangam contributed to API(```__init.py__```), test file(```test_flaskr.py```).
- The project and other files are credicted to [Udacity](https://www.udacity.com/course/full-stack-web-developer-nanodegree--nd0044)

## Testing
To run the tests, run
```
dropdb trivia_test
createdb trivia_test
psql trivia_test < trivia.psql
python test_flaskr.py
```
