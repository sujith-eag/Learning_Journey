
Express.js app using **EJS** that renders a **movie gallery** with:
* A layout containing **header/footer**.
* **External CSS** for styling.
* **Conditional rendering** to highlight movies with ratings above 8.

### Project Structure

```
movie-gallery/
├── public/
│   └── styles.css
├── views/
│   ├── layout.ejs
│   └── index.ejs
├── app.js
├── package.json
```

---


Create a `package.json`,install `express` and `ejs`


## `app.js`

```js
import express from 'express';
const app = express();
const path = require('path');

// Setting EJS as templating engine
app.set('view engine', 'ejs');
app.set('views', path.join(__dirname, 'views'));

// Serve static files from public (CSS)
app.use(express.static(path.join(__dirname, 'public') ));

const movies = [
  { title: "Inception", rating: 8.8 },
  { title: "The Room", rating: 3.7 },
  { title: "Interstellar", rating: 8.6 },
  { title: "Jumanji", rating: 6.9 }
];

// Route
app.get('/', (req, res) => {
  res.render('index', { movies });
});


app.listen(3000, () => {
  console.log('Server running on http://localhost:3000');
});
```

## `views/layout.ejs`

Base layout with header/footer.

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Movie Gallery</title>
  <link rel="stylesheet" href="/styles.css">
</head>
<body>
  <header>
    <h1>Movie Gallery</h1>
  </header>

  <main>
    <%- body %>
  </main>

  <footer>
    <p>&copy; 2025 Movie Gallery</p>
  </footer>
</body>
</html>
```

## `views/index.ejs`

Render movies and highlight those with rating > 8.

```html
<% layout('layout') %>

<div class="gallery">
  <% movies.forEach(movie => { %>
    <div class="card <%= movie.rating > 8 ? 'highlight' : '' %>">
      <h2><%= movie.title %></h2>
      <p>Rating: <%= movie.rating %></p>
    </div>
  <% }) %>
</div>
```

Note: If you're not using a layout manager like `express-ejs-layouts`, you can replace `<% layout('layout') %>` with:

```ejs
<%- include('layout', { body: include('index') }) %>
```

Or embed directly into `layout.ejs` using a `<%- body %>` placeholder (as already done above), and render `index.ejs` with layout content only.

To simplify, you can skip layout libraries and just **copy-paste the layout in `index.ejs`**, but this example assumes one base layout file.

## `public/styles.css`

```css
body {
  font-family: Arial, sans-serif;
  background-color: #f9f9f9;
  margin: 0;
  padding: 0;
}

header, footer {
  background-color: #222;
  color: white;
  text-align: center;
  padding: 1em 0;
}

.gallery {
  display: flex;
  justify-content: center;
  flex-wrap: wrap;
  padding: 2em;
  gap: 1em;
}

.card {
  background-color: white;
  padding: 1em;
  border: 1px solid #ddd;
  border-radius: 5px;
  width: 200px;
  box-shadow: 2px 2px 5px rgba(0,0,0,0.1);
  text-align: center;
}

.card.highlight {
  background-color: #e0ffe0;
  border-color: #00cc00;
}
```

