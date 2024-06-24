<template>
    <section class="wrapper">
      <div class="spinner">
        <i></i>
        <i></i>
        <i></i>
        <i></i>
        <i></i>
        <i></i>
        <i></i>
      </div>
    </section>
  </template>
  
  <style scoped>
  /* Import necessary CSS imports directly here if needed */
  
  /* Variables */
  :root {
    --colors: #2172b8, #18a39b, #82c545, #f8b739, #f06045, #ed2861, #c12680, #5d3191;
    --inner: 30px;
    --border: 6px;
    --spacing: 1px;
  }
  
  /* Global box-sizing */
  * {
    -webkit-box-sizing: border-box;
    -moz-box-sizing: border-box;
    box-sizing: border-box;
  }
  
  /* Wrapper styling */
  section.wrapper {
    padding: 40px 0;
    background: #313134; /* dark background color */
  }
  
  /* Spinner styling */
  div.spinner {
    animation: rotate 10s infinite linear;
    position: relative;
    display: block;
    margin: auto;
  
    /* Calculate size based on number of colors */
    --size: calc(var(--inner) + calc(8 * (var(--border) + var(--spacing)))); /* 8 is the number of colors */
  
    width: var(--size);
    height: var(--size);
  }
  
  /* Individual spinner item styling */
  div.spinner i {
    animation: rotate 3s infinite cubic-bezier(0.09, 0.6, 0.8, 0.03);
    transform-origin: 50% 100% 0;
    position: absolute;
    display: inline-block;
    top: 50%;
    left: 50%;
    border: solid var(--border) transparent;
    border-bottom: none;
  }
  
  /* Color-specific styling */
  div.spinner i:nth-child(1) {
    --size: calc(var(--inner) + calc(1 * (var(--border) + var(--spacing))));
    animation-timing-function: cubic-bezier(0.09, 0.3, 0.12, 0.03);
    width: var(--size);
    height: calc(var(--size) / 2);
    margin-top: calc(-1 * var(--size) / 2);
    margin-left: calc(-1 * var(--size) / 2);
    border-color: #2172b8; /* Adjust color */
  }
  
  /* Repeat for other colors as needed */
  /* div.spinner i:nth-child(2) ... */
  
  /* Keyframes for rotation animation */
  @keyframes rotate {
    to {
      transform: rotateZ(360deg);
    }
  }
  </style>
  