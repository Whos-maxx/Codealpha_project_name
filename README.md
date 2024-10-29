# Codealpha_project_name
html
Copy code
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Image Gallery</title>
  <style>
    /* Basic styling for the gallery layout */
    body {
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
      margin: 0;
      font-family: Arial, sans-serif;
      background-color: #f0f0f0;
    }
    .gallery-container {
      width: 80%;
      max-width: 700px;
      position: relative;
    }
    .gallery-image {
      width: 100%;
      height: auto;
      border-radius: 8px;
      box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
    }
    .gallery-buttons {
      display: flex;
      justify-content: space-between;
      position: absolute;
      top: 50%;
      width: 100%;
      transform: translateY(-50%);
    }
    .gallery-buttons button {
      background-color: rgba(0, 0, 0, 0.5);
      border: none;
      color: white;
      font-size: 18px;
      padding: 8px 16px;
      cursor: pointer;
      transition: background-color 0.3s;
    }
    .gallery-buttons button:hover {
      background-color: rgba(0, 0, 0, 0.7);
    }
    .thumbnail-container {
      display: flex;
      justify-content: center;
      margin-top: 10px;
    }
    .thumbnail {
      width: 60px;
      height: 60px;
      margin: 5px;
      cursor: pointer;
      opacity: 0.6;
      border-radius: 4px;
    }
    .thumbnail.active {
      border: 2px solid #007bff;
      opacity: 1;
    }
  </style>
</head>
<body>

<div class="gallery-container">
  <img id="mainImage" class="gallery-image" src="https://via.placeholder.com/700x400?text=Image+1" alt="Gallery Image">

  <div class="gallery-buttons">
    <button onclick="prevImage()">❮ Prev</button>
    <button onclick="nextImage()">Next ❯</button>
  </div>

  <div class="thumbnail-container">
    <img class="thumbnail active" src="https://via.placeholder.com/700x400?text=Image+1" onclick="setImage(0)">
    <img class="thumbnail" src="https://via.placeholder.com/700x400?text=Image+2" onclick="setImage(1)">
    <img class="thumbnail" src="https://via.placeholder.com/700x400?text=Image+3" onclick="setImage(2)">
    <img class="thumbnail" src="https://via.placeholder.com/700x400?text=Image+4" onclick="setImage(3)">
    <img class="thumbnail" src="https://via.placeholder.com/700x400?text=Image+5" onclick="setImage(4)">
  </div>
</div>

<script>
  // JavaScript to handle image navigation
  const images = [
    "https://via.placeholder.com/700x400?text=Image+1",
    "https://via.placeholder.com/700x400?text=Image+2",
    "https://via.placeholder.com/700x400?text=Image+3",
    "https://via.placeholder.com/700x400?text=Image+4",
    "https://via.placeholder.com/700x400?text=Image+5"
  ];

  let currentIndex = 0;

  function updateMainImage(index) {
    const mainImage = document.getElementById("mainImage");
    mainImage.src = images[index];
    updateThumbnails(index);
  }

  function updateThumbnails(index) {
    const thumbnails = document.querySelectorAll(".thumbnail");
    thumbnails.forEach((thumb, i) => {
      thumb.classList.toggle("active", i === index);
    });
  }

  function nextImage() {
    currentIndex = (currentIndex + 1) % images.length;
    updateMainImage(currentIndex);
  }

  function prevImage() {
    currentIndex = (currentIndex - 1 + images.length) % images.length;
    updateMainImage(currentIndex);
  }

  function setImage(index) {
    currentIndex = index;
    updateMainImage(index);
  }

  // Initialize gallery
  updateMainImage(currentIndex);
</script>

</body>
</html>
