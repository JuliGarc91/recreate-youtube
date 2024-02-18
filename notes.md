# Building Youtube Kinda

To build this React application you'll need to integrate several key elements, including React Router for navigation, the YouTube API for video searches, and potentially Bootstrap for styling if you choose to use it. Below, is the general structure and code snippets to help you get started on this project.

## Project Structure

Your project structure might look something like this:

```
my-app/
├── src/
│   ├── components/
│   │   ├── About.js
│   │   ├── Home.js
│   │   ├── NavBar.js
│   │   ├── SearchResults.js
│   │   ├── ShowVideo.js
│   │   ├── VideoList.js
│   │   └── CommentForm.js
│   ├── App.js
│   ├── index.js
│   └── styles/
│       ├── App.css
│       └── NavBar.css
├── public/
│   └── index.html
└── package.json
```

## Key Implementation Steps

1. **Set up React Router**:
   - Install React Router by running `npm install react-router-dom@6.2.1`.
   - In your `App.js`, import `BrowserRouter`, `Routes`, and `Route` from `react-router-dom` to set up your routes.

2. **Create Components**:
   - **NavBar**: Contains links to Home and About pages.
   - **Home**: Includes a search bar and displays search results.
   - **About**: Contains information about the developers.
   - **SearchResults**: Displays video thumbnails and titles.
   - **ShowVideo**: Displays a larger version of the video and the comment form.
   - **CommentForm**: Allows users to post comments.

3. **YouTube API Integration**:
   - Obtain an API key from the Google Developer Console for the YouTube API.
   - Use the `fetch` API or `axios` to retrieve video data based on user searches from the Home page.

4. **Implementing the Search Feature**:
   - Use a state in the Home component to manage the search query and search results.
   - Make an API call to YouTube upon form submission to retrieve video data.
   - Pass the search results to the `SearchResults` component to display them.

5. **Video Show Page**:
   - Use the `useParams` hook from React Router to retrieve the video ID from the URL.
   - Fetch and display the video details on the ShowVideo page.

6. **Commenting Feature**:
   - In the `ShowVideo` component, include the `CommentForm` component.
   - Implement form validation to ensure neither the name nor comment fields are empty before submission.

7. **Responsive Design**:
   - Use CSS or Bootstrap for styling. If using Bootstrap, you can install it via npm and import it into your project.

8. **Navigation with React Router**:
   - Use `Link` components in the NavBar for navigation.
   - Dynamic routing for the video show page, capturing video IDs.

### Sample Code Snippets

- **App.js**: Setting up routes

```jsx
import React from 'react';
import { BrowserRouter, Routes, Route } from 'react-router-dom';
import Home from './components/Home';
import About from './components/About';
import NavBar from './components/NavBar';
import ShowVideo from './components/ShowVideo';

function App() {
  return (
    <BrowserRouter>
      <NavBar />
      <Routes>
        <Route path="/" element={<Home />} />
        <Route path="/about" element={<About />} />
        <Route path="/video/:videoId" element={<ShowVideo />} />
      </Routes>
    </BrowserRouter>
  );
}
```

- **NavBar.js**: Navigation bar with links

```jsx
import React from 'react';
import { Link } from 'react-router-dom';

const NavBar = () => (
  <nav>
    <Link to="/">Home</Link>
    <Link to="/about">About</Link>
  </nav>
);

export default NavBar;
```
## API Key

To obtain an API key from the Google Developer Console for the YouTube API, follow these steps. This process will allow you to access various YouTube API services, such as retrieving video details, managing playlists, and more.

1. **Create a Google Cloud Project**:
   - Visit the [Google Cloud Console](https://console.cloud.google.com/).
   - Sign in with your Google account if you haven't already.
   - Click on the project dropdown near the top of the page to create a new project.
   - Click on the "New Project" button, give your project a name, and click "Create".

2. **Enable the YouTube Data API v3**:
   - With your project selected, navigate to the "APIs & Services > Dashboard" section from the left sidebar.
   - Click on "+ ENABLE APIS AND SERVICES" at the top.
   - Search for "YouTube Data API v3" in the API Library.
   - Click on the YouTube Data API v3 and then click the "Enable" button to enable the API for your project.

3. **Create an API Key**:
   - After enabling the YouTube Data API, go to the "Credentials" tab on the left sidebar.
   - Click on "+ CREATE CREDENTIALS" at the top and select "API key" from the dropdown menu.
   - The API key will be created and shown to you. You can restrict the key's usage to specific IP addresses, referrers, or APIs for security purposes.

4. **(Optional) Restrict the API Key**:
   - After creating the API key, you can click on it to see the key's details.
   - Here, you can set application restrictions (e.g., HTTP referrers, IP addresses) and API restrictions (limit the key to only be used with the YouTube Data API v3).

5. **Copy Your API Key**:
   - Once your API key is created (and optionally restricted), make sure to copy it and keep it secure. You will use this key in your application to authenticate API requests.

Remember, API keys are sensitive information. Treat them like passwords and keep them secure. Do not share your API keys in public repositories or with untrusted parties.

By following these steps, you will have successfully obtained an API key for the YouTube Data API and will be ready to integrate YouTube data into your applications.

### When you need to use your api key you will do something like this

```js
fetch(
  `https://youtube.googleapis.com/youtube/v3/search?key=${import.meta.env.VITE_APP_API_KEY}`
);
```

This outline and the provided snippets should help you get started on your application. Remember to replace placeholders and example codes with actual data and functionalities specific to your project requirements.