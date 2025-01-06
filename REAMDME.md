1. Debouncing

Debouncing ensures that a function is executed only after a specified delay has passed since the last time it was triggered. 
This is useful when you want to delay execution until a user has finished performing a series of actions.

example :

function debounce(func, delay) {
  let timer;
  return function (...args) {
    clearTimeout(timer); // Reset timer
    timer = setTimeout(() => func.apply(this, args), delay); // Set new timer
  };
}

function searchQuery(query) {
  console.log(`Searching for: ${query}`);
  const resultsDiv = document.getElementById("results");
  resultsDiv.textContent = `Results for "${query}"`;
}


const debouncedSearch = debounce(searchQuery, 500);


const searchBox = document.getElementById("search-box");
searchBox.addEventListener("input", (event) => {
  debouncedSearch(event.target.value);
});

  
  
  2. Throttling

Throttling ensures that a function is executed at most once every specified time interval, 
regardless of how often the event is triggered. This is useful for limiting the rate of execution.

example :

function throttle(func, limit) {
  let lastCall = 0;
  return function (...args) {
    const now = Date.now();
    if (now - lastCall >= limit) {
      lastCall = now;
      func.apply(this, args);
    }
  };
}


function searchQuery(query) {
  console.log(`Searching for: ${query}`);
  const resultsDiv = document.getElementById("results");
  resultsDiv.textContent = `Results for "${query}"`;
}


const throttledSearch = throttle(searchQuery, 1000);

const searchBox = document.getElementById("search-box");
searchBox.addEventListener("input", (event) => {
  throttledSearch(event.target.value);
});

