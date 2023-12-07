# irenesproject

LINK TO REPL:
https://replit.com/@IreneKandio/FriendsWinners

main.py
from flask import Flask, render_template

# Your existing data here
friends_awards_data = {
    "Brad Pitt": {
        "photo_url": "/images/BradPitt.jpeg",
        "awards": "List of Brad Pitt's awards"
    },
    "Jennifer Aniston": {
        "photo_url": "/images/JennAniston.jpeg",
        "awards": "List of Jennifer Aniston's awards"
    },
     "Lisa kudrow": {
      "photo_url": "/images/LisaKudrow.webp",
      "awards": "List of Lisa Kudrow's awards"
  },
  "Julia Roberts": {
      "photo_url": "/images/Julia_Roberts.jpeg",
      "awards": "List of Julia Robert's awards"
  },
    "Reese Witherspoon": {
        "photo_url": "/images/ReeseWitherspoon.jpeg",
        "awards": "List of Reese Witherspoon's awards"
    },
  "George Clooney": {
      "photo_url": "/images/GeorgeClooney.jpg",
      "awards": "List of George Clooney's awards"
  }
}

# Flask setup starts here
app = Flask(__name__)

@app.route('/')
def home():
    return render_template('index.html', friends_awards_data=friends_awards_data)

if __name__ == "__main__":
    app.run(debug=True)

index.html
<!DOCTYPE html>
<html>
<head>
    <!-- Your head info here -->
    <title>Your title</title>
</head>
<body>
    <!-- Loop through each actor in the dictionary -->
    {% for actor, details in friends_awards_data.items() %}
        <div>
            <h1>{{actor}}</h1>
            <!-- Use the actor's 'photo_url' attribute as the source for an image -->
            <img src="{{ details['photo_url'] }}" alt="Photo of {{ Brad Pitt }}" />
            <p>{{details['awards']}}</p>
        </div>    
    {% endfor %}
    <!-- MORE TO AD -->
</body>
</html>

main.js
// Array of actors
const actors = ['Jennifer Aniston', 'Lisa Kudrow', 'Brad Pitt', 'Courteney Cox', 'Reese Witherspoon', 'Julia Roberts', 'George Clooney'];

// Function to fetch news about an actor
function fetchNews(actor) {
    const url = `https://newsapi.org/v2/everything?q=${actor}&apiKey=1d5206dea21747a99bfd63c2e1ce066f`;

    fetch(url)
    .then(response => {
        if (!response.ok) {
            throw new Error(`HTTP error! status: ${response.status}`);
        }
        return response.json();
    })
    .then(data => {
        console.log(`News about ${actor}:`);
        data.articles.forEach(article => {
            console.log(`Title: ${article.title}`);
        });
    })
    .catch(e => {
        console.log('There was a problem with the fetch operation: ' + e.message);
    });
}

// Call fetchNews for each actor
actors.forEach(fetchNews);

styles.css
body {
    font-family: Arial, sans-serif;
}

h1 {
    text-align: center;
}

.actor {
    margin-bottom: 20px;
}

.actor h2 {
    color: #333;
}

.actor img {
    width: 200px;
    height: 200px;
}

.article {
    margin-bottom: 10px;
    border-bottom: 1px solid #ddd;
    padding-bottom: 10px;
}
