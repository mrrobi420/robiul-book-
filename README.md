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
      font-size: 24px;
    }
    .container {
      display: flex;
      justify-content: center;
      margin-top: 20px;
    }
    .profile, .feed {
      background: white;
      padding: 20px;
      border-radius: 10px;
      margin: 10px;
    }
    .profile {
      width: 250px;
    }
    .feed {
      width: 500px;
    }
    .post {
      background: #f0f2f5;
      padding: 10px;
      border-radius: 8px;
      margin-bottom: 10px;
    }
    input, textarea {
      width: 100%;
      padding: 8px;
      margin-bottom: 10px;
      border-radius: 5px;
      border: 1px solid #ccc;
    }
    button {
      background-color: #4267B2;
      color: white;
      border: none;
      padding: 10px;
      border-radius: 5px;
      cursor: pointer;
    }
    button:hover {
      background-color: #365899;
    }
  </style>
</head>
<body>

  <header>RobiulBook</header>

  <div class="container">
    <div class="profile">
      <h3>Robiul</h3>
      <p>🌟 Your status: Online</p>
      <p>📍 Location: Bangladesh</p>
    </div>

    <div class="feed">
      <h3>What's on your mind?</h3>
      <textarea id="postInput" placeholder="Type something..."></textarea>
      <button onclick="addPost()">Post</button>

      <div id="posts"></div>
    </div>
  </div>

  <script>
    function addPost() {
      const input = document.getElementById('postInput');
      const postsDiv = document.getElementById('posts');
      if(input.value.trim() === '') return;

      const post = document.createElement('div');
      post.className = 'post';
      post.textContent = input.value;

      postsDiv.prepend(post);
      input.value = '';
    }
  </script>

</body>
</html>
