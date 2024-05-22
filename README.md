# JavaScript Smooth Scrolling

This JavaScript code provides a smooth scrolling experience for anchor links on your webpage. It overrides the default "jump" behavior and smoothly animates the scroll to the target section.

## Features

- Smooth scrolling for anchor links (`<a href="#section-id">`).
- Customizable scroll duration and speed.
- Easy to integrate into your website's JavaScript.

## Demo

[https://leartme.com/]

## How to Use

1. **HTML:**

   Ensure your anchor links have appropriate `href` attributes pointing to the ID of the target section (e.g., `<a href="#about">About</a>`).

2. **JavaScript:**

   Add the following JavaScript code to your webpage (e.g., within a `<script>` tag in the `<head>` or before the closing `</body>` tag):

```javascript
document.querySelectorAll('a[href^="#"]').forEach(anchor => {
  anchor.addEventListener('click', function (e) {
    e.preventDefault(); 

    const targetId = this.getAttribute('href');
    const targetElement = document.querySelector(targetId);

    // Custom smooth scrolling function
    const scrollDuration = 1000; // Duration in milliseconds (adjust as needed)
    const scrollStep = 50;       // Smaller step means slower scrolling
    const scrollOffset = targetElement.getBoundingClientRect().top;
    let currentPosition = window.pageYOffset;

    const smoothScroll = setInterval(() => {
      if (currentPosition < scrollOffset) {
        currentPosition += scrollStep;
        if (currentPosition > scrollOffset) currentPosition = scrollOffset;
      } else {
        currentPosition -= scrollStep;
        if (currentPosition < scrollOffset) currentPosition = scrollOffset;
      }
      window.scrollTo(0, currentPosition);

      if (currentPosition === scrollOffset) {
        clearInterval(smoothScroll);
      }
    }, 16); // 16ms for approximately 60fps
  });
});
```
## Customization
**Scroll Duration:** Adjust the `scrollDuration` variable (in milliseconds) to control how long the scrolling animation takes.

**Scroll Step:** Modify the `scrollStep` variable to change the speed of the scrolling animation. Smaller values make it slower.

## Compatibility
This code should work in all modern browsers. For older browsers like Internet Explorer, you might need a polyfill for the `forEach` method or use a slightly different approach.
