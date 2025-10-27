# MWAD_EX05_image-carousel-in-react
## Date:

## AIM
To create a Image Carousel using React 

## ALGORITHM
### STEP 1 Initial Setup:
Input: A list of images to display in the carousel.

Output: A component displaying the images with navigation controls (e.g., next/previous buttons).

### Step 2 State Management:
Use a state variable (currentIndex) to track the index of the current image displayed.

The carousel starts with the first image, so initialize currentIndex to 0.

### Step 3 Navigation Controls:
Next Image: When the "Next" button is clicked, increment currentIndex.

If currentIndex is at the end of the image list (last image), loop back to the first image using modulo:
currentIndex = (currentIndex + 1) % images.length;

Previous Image: When the "Previous" button is clicked, decrement currentIndex.

If currentIndex is at the beginning (first image), loop back to the last image:
currentIndex = (currentIndex - 1 + images.length) % images.length;

### Step 4 Displaying the Image:
The currentIndex determines which image is displayed.

Using the currentIndex, display the corresponding image from the images list.

### Step 5 Auto-Rotation:
Set an interval to automatically change the image after a set amount of time (e.g., 3 seconds).

Use setInterval to call the nextImage() function at regular intervals.

Clean up the interval when the component unmounts using clearInterval to prevent memory leaks.

## PROGRAM
# HTML
```
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Pure JavaScript Image Carousel</title>
  <style>
    body {
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
      background: #222;
      margin: 0;
    }

    .carousel {
      position: relative;
      width: 600px;
      height: 350px;
      overflow: hidden;
      border-radius: 10px;
      box-shadow: 0 4px 10px rgba(0,0,0,0.5);
    }

    .carousel img {
      width: 100%;
      height: 100%;
      object-fit: cover;
      display: none;
    }

    .carousel img.active {
      display: block;
    }

    button {
      position: absolute;
      top: 50%;
      transform: translateY(-50%);
      background: rgba(255,255,255,0.6);
      border: none;
      font-size: 24px;
      padding: 8px 12px;
      border-radius: 50%;
      cursor: pointer;
    }

    button:hover {
      background: white;
    }

    .prev { left: 10px; }
    .next { right: 10px; }
  </style>
</head>
<body>

  <div id="carousel"></div>

  <script>
    // --- Image sources ---
    const imageSources = [
      "https://picsum.photos/id/1018/600/350",
      "https://picsum.photos/id/1025/600/350",
      "https://picsum.photos/id/1033/600/350",
      "https://picsum.photos/id/1041/600/350"
    ];

    // --- Create carousel elements ---
    const carousel = document.getElementById('carousel');
    carousel.classList.add('carousel');

    const prevBtn = document.createElement('button');
    prevBtn.textContent = '❮';
    prevBtn.className = 'prev';

    const nextBtn = document.createElement('button');
    nextBtn.textContent = '❯';
    nextBtn.className = 'next';

    // --- Add images ---
    imageSources.forEach((src, i) => {
      const img = document.createElement('img');
      img.src = src;
      if (i === 0) img.classList.add('active');
      carousel.appendChild(img);
    });

    // Add buttons
    carousel.appendChild(prevBtn);
    carousel.appendChild(nextBtn);

    // --- JS functionality ---
    const images = carousel.querySelectorAll('img');
    let index = 0;

    function showImage(n) {
      images.forEach(img => img.classList.remove('active'));
      images[n].classList.add('active');
    }

    nextBtn.addEventListener('click', () => {
      index = (index + 1) % images.length;
      showImage(index);
    });

    prevBtn.addEventListener('click', () => {
      index = (index - 1 + images.length) % images.length;
      showImage(index);
    });

    // Auto-slide every 3 seconds
    setInterval(() => {
      index = (index + 1) % images.length;
      showImage(index);
    }, 3000);
  </script>

</body>
</html>

```


## OUTPUT
<img width="1285" height="943" alt="image" src="https://github.com/user-attachments/assets/4ae35322-cd70-443e-a734-e3c8418e51d9" />

<img width="1274" height="931" alt="image" src="https://github.com/user-attachments/assets/04e12b4a-01d0-4541-9a80-ac047e44cf11" />


## RESULT
The program for creating Image Carousel using React is executed successfully.
