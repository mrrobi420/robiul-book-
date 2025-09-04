<!DOCTYPE html>
<html lang="bn">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>RobiulBook</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background-color: #f0f2f5;
      margin: 0;
      padding: 0;
    }

    header {
      background-color: #4267B2;
      color: white;
      padding: 15px;
      text-align: center;
      font-size: 26px;
      font-weight: bold;
    }

    .container {
      display: flex;
      justify-content: center;
      margin-top: 20px;
      gap: 20px;
      flex-wrap: wrap;
    }

    .profile, .feed {
      background: white;
      padding: 20px;
      border-radius: 10px;
      box-shadow: 0 2px 5px rgba(0,0,0,0.1);
    }

    .profile {
      width: 250px;
      text-align: center;
    }

    .profile img {
      width: 120px;
      height: 120px;
      border-radius: 50%;
      margin-bottom: 10px;
    }

    .feed {
      width: 500px;
    }

    textarea {
      width: 100%;
      padding: 10px;
      border-radius: 8px;
      border: 1px solid #ccc;
      margin-bottom: 10px;
      resize: none;
    }

    button {
      background-color: #4267B2;
      color: white;
      border: none;
      padding: 10px 20px;
      border-radius: 5px;
      cursor: pointer;
    }

    button:hover {
      background-color: #365899;
    }

    .post {
      background: #f0f2f5;
      padding: 10px;
      border-radius: 8px;
      margin-bottom: 10px;
    }

    .post p {
      margin: 0;
      margin-bottom: 5px;
    }

    .actions {
      display: flex;
      gap: 10px;
    }

    .comment-input {
      width: 100%;
      padding: 5px;
      border-radius: 5px;
      border: 1px solid #ccc;
      margin-top: 5px;
    }
  </style>
</head>
<body>

  <header>RobiulBook</header>

  <div class="container">
    <div class="profile">
      <img src="https://via.placeholder.com/120" alt="Profile Picture">
      <h3>Robiul</h3>
      <p>🌟 Online</p>
      <p>📍 Bangladesh</p>
    </div>

    <div class="feed">
      <h3>What's on your mind?</h3>
      <textarea id="postInput" rows="3" placeholder="Type something..."></textarea>
      <button onclick="addPost()">Post</button>

      <div id="posts"></div>
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

      // Actions: Like + Comment
      const actionsDiv = document.createElement('div');
      actionsDiv.className = 'actions';

      const likeBtn = document.createElement('button');
      likeBtn.textContent = 'Like ❤️';
      likeBtn.onclick = function() {
        likeBtn.textContent = likeBtn.textContent === 'Like ❤️' ? 'Liked 👍' : 'Like ❤️';
      }

      actionsDiv.appendChild(likeBtn);

      // Comment input
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
