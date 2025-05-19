# Ex05 Image Carousel
## Date:19/05/2025

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
# Carousel.js
'''
import React, { useState, useEffect } from 'react';
import './Carousel.css';

const images = [
  '/images/img1.jpg',
  '/images/img2.jpeg',
  '/images/img3.jpeg',
];

const Carousel = () => {
  const [currentIndex, setCurrentIndex] = useState(0);

  const nextImage = () => {
    setCurrentIndex((currentIndex + 1) % images.length);
  };

  const prevImage = () => {
    setCurrentIndex((currentIndex - 1 + images.length) % images.length);
  };

  useEffect(() => {
    const interval = setInterval(nextImage, 3000);
    return () => clearInterval(interval); // Cleanup on unmount
  }, [currentIndex]);

  return (
    <div className="carousel-container">
      <img src={images[currentIndex]} alt="carousel" className="carousel-image" />
      <div className="controls">
        <button onClick={prevImage}>Previous</button>
        <button onClick={nextImage}>Next</button>
      </div>
    </div>
    
  );
};

export default Carousel;
'''
#Carousel.css
'''css
.carousel-container {
  position: relative;
  width: 80%;
  max-width: 800px;
  margin: 0 auto;
  padding: 20px;
  box-shadow: 0 4px 15px rgba(0, 0, 0, 0.2);
  border-radius: 12px;
  background-color: #f9f9f9;
}

.carousel-image {
  width: 100%;
  height: 400px;
  object-fit: cover;
  border-radius: 10px;
  transition: opacity 0.5s ease-in-out;
}

.controls {
  margin-top: 15px;
  display: flex;
  justify-content: center;
  gap: 20px;
}

.controls button {
  padding: 10px 20px;
  background-color: #007bff;
  color: white;
  border: none;
  border-radius: 8px;
  font-size: 16px;
  cursor: pointer;
  transition: background-color 0.3s ease;
}

.controls button:hover {
  background-color: #0056b3;
}
'''
#App.js
'''
import React from 'react';
import './App.css';
import Carousel from './components/Carousel';
import Footer from './components/Footer'; // 

function App() {
  return (
    <div className="App">
      <h1>Image Carousel</h1>
      <Carousel />
      <Footer /> {/* 
 */}
    </div>
  );
}

export default App;
'''
#App.css
'''
.App {
  text-align: center;
}

.App-logo {
  height: 40vmin;
  pointer-events: none;
}

@media (prefers-reduced-motion: no-preference) {
  .App-logo {
    animation: App-logo-spin infinite 20s linear;
  }
}

.App-header {
  background-color: #282c34;
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  font-size: calc(10px + 2vmin);
  color: white;
}

.App-link {
  color: #61dafb;
}

@keyframes App-logo-spin {
  from {
    transform: rotate(0deg);
  }
  to {
    transform: rotate(360deg);
  }
}
'''
# Footer.js
'''
import React from 'react';
import './Footer.css';

const Footer = () => {
  return (
    <footer className="footer">
     <p>yogesh 212222040185</p>
      <p>&copy; {new Date().getFullYear()} Image Carousel App. All rights reserved.</p>
    </footer>
  );
};

export default Footer;
'''
#Footer.css
'''
.footer {
    background-color: #222;
    color: #fff;
    text-align: center;
    padding: 15px 0;
    position: relative;
    bottom: 0;
    width: 100%;
    margin-top: 40px;
    font-size: 14px;
  }
'''

## OUTPUT


## RESULT
The program for creating Image Carousel using React is executed successfully.
