<!DOCTYPE html>
<html lang="bn">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>RobiulBook</title>
<style>
  body {
    margin: 0;
    font-family: Arial, sans-serif;
    background-color: #f0f2f5;
  }

  /* Header */
  header {
    background-color: #4267B2;
    color: white;
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 10px 20px;
    position: sticky;
    top: 0;
    z-index: 1000;
  }

  header h1 {
    margin: 0;
    font-size: 24px;
  }

  header input {
    padding: 5px 10px;
    border-radius: 20px;
    border: none;
    width: 200px;
  }

  header .profile-nav img {
    width: 40px;
    height: 40px;
    border-radius: 50%;
  }

  /* Main layout */
  .main {
    display: flex;
    justify-content: center;
    gap: 20px;
    margin-top: 20px;
    flex-wrap: wrap;
  }

  /* Left Sidebar */
  .sidebar {
    width: 250px;
    background: white;
    border-radius: 10px;
    padding: 20px;
    height: fit-content;
  }

  .sidebar img {
    width: 100%;
    border-radius: 10px;
    margin-bottom: 10px;
  }

  .sidebar h3 {
    margin-top: 0;
  }

  .sidebar ul {
    list-style: none;
    padding: 0;
  }

  .sidebar ul li {
    margin: 10px 0;
    cursor: pointer;
  }

  /* Feed */
  .feed {
    width: 500px;
    display: flex;
    flex-direction: column;
    gap: 20px;
  }

  .stories {
    display: flex;
    gap: 10px;
    background: white;
    padding: 10px;
    border-radius: 10px;
    overflow-x: auto;
  }

  .story {
    min-width: 80px;
    height: 120px;
    background: #ccc;
    border-radius: 10px;
    text-align: center;
    padding-top: 90px;
    font-weight: bold;
    cursor: pointer;
  }

  .post-box, .post {
    background: white;
    padding: 10px;
    border-radius: 10px;
  }

  .post-box textarea {
    width: 100%;
    padding: 10px;
    border-radius: 10px;
    border: 1px solid #ccc;
    resize: none;
  }

  .post-box button {
    margin-top: 10px;
    padding: 10px 15px;
    border: none;
    border-radius: 5px;
    background-color: #4267B2;
    color: white;
    cursor: pointer;
  }

  .post .actions {
    display: flex;
    gap: 10px;
    margin-top: 5px;
  }

  .post .comment-input {
    width: 100%;
    margin-top: 5px;
    padding: 5px;
    border-radius: 5px;
    border: 1px solid #ccc;
  }

  /* Right Sidebar */
  .right-sidebar {
    width: 250px;
    background: white;
    padding: 20px;
    border-radius: 10px;
    height: fit-content;
  }

  .right-sidebar h3 {
    margin-top: 0;
  }

  /* Scrollbar styling for stories */
  .stories::-webkit-scrollbar {
    height: 6px;
  }

  .stories::-webkit-scrollbar-thumb {
    background-color: #888;
    border-radius: 3px;
  }
</style>
</head>
<body>

<header>
  <h1>RobiulBook</h1>
  <input type="text" placeholder="Search RobiulBook">
  <div class="profile-nav">
    <img src="https://via.placeholder.com/40" alt="Profile">
  </div>
</header>

<div class="main">
  <!-- Left Sidebar -->
  <div class="sidebar">
    <img src="https://via.placeholder.com/250x120" alt="Cover Photo">
    <h3>Robiul</h3>
    <ul>
      <li>Profile</li>
      <li>Friends</li>
      <li>Groups</li>
      <li>Marketplace</li>
      <li>Settings</li>
    </ul>
  </div>

  <!-- Feed -->
  <div class="feed">
    <!-- Stories -->
    <div class="stories">
      <div class="story">Story 1</div>
      <div class="story">Story 2</div>
      <div class="story">Story 3</div>
      <div class="story">Story 4</div>
      <div class="story">Story 5</div>
    </div>

    <!-- Post Box -->
    <div class="post-box">
      <textarea id="postInput" rows="3" placeholder="What's on your mind?"></textarea>
      <button onclick="addPost()">Post</button>
    </div>

    <!-- Posts -->
    <div id="posts"></div>
  </div>

  <!-- Right Sidebar -->
  <div class="right-sidebar">
    <h3>Friend Suggestions</h3>
    <ul>
      <li>Friend 1</li>
      <li>Friend 2</li>
      <li>Friend 3</li>
    </ul>

    <h3>Trending</h3>
    <ul>
      <li>Topic 1</li>
      <li>Topic 2</li>
      <li>Topic 3</li>
    </ul>
  </div>
</div>

<script>
function addPost() {
  const input = document.getElementById('postInput');
  const postsDiv = document.getElementById('posts');

  if(input.value.trim() === '') return;

  const postDiv = document.createElement('div');
  postDiv.className = 'post';

  const postContent = document.createElement('p');
  postContent.textContent = input.value;
  postDiv.appendChild(postContent);

  const actionsDiv = document.createElement('div');
  actionsDiv.className = 'actions';

  const likeBtn = document.createElement('button');
  likeBtn.textContent = 'Like ❤️';
  likeBtn.onclick = function() {
    likeBtn.textContent = likeBtn.textContent === 'Like ❤️' ? 'Liked 👍' : 'Like ❤️';
  }

  actionsDiv.appendChild(likeBtn);

  const commentInput = document.createElement('input');
  commentInput.className = 'comment-input';
  commentInput.placeholder = 'Write a comment...';
  commentInput.onkeypress = function(e) {
    if(e.key === 'Enter' && commentInput.value.trim() !== '') {
      const comment = document.createElement('p');
      comment.textContent = '💬 ' + commentInput.value;
      comment.style.marginLeft = '10px';
      postDiv.appendChild(comment);
      commentInput.value = '';
    }
  }

  postDiv.appendChild(actionsDiv);
  postDiv.appendChild(commentInput);

  postsDiv.prepend(postDiv);
  input.value = '';
}
</script>

</body>
</html>
