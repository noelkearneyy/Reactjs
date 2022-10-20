# Intersection Observer API
- Elements should be initially hidden - opacity of zero. 
- Create a show class which will be added to each of the elements you wish to transition. 
- As soon as the selected elements shows onto the screen we want to add the show class.

```
const elements = document.querySelectorAll('.selected-class');

const observer = new IntersectionObserver(enteries=>{
  enteries.forEach(entry => {
    entry.target.classList.toggle('show', entry.isIntersecting)
    // Will stop animation when scrolling up
    if(entry.isIntersecting) observer.unobserve(entry.target)
  }) 
}, {
  threshold: 1,
  // Offset something by default 
  rootMargin: '-100px',
  // You can define the actual container - scrolling container
  root: ''
});

cards.forEach(card => {
  observer.observe(card);
})

```
- IntersectionRatio - What percentage of this object is on the screen; 1 = 100%.
- isIntersection - Will be True if it is on the screen and is visible to the user. 
- boundingClientRect - The shape of the element. 
- intersectionRect - Amount of space visible on the screen of the element.
- rootBounds - The bounds of the screen. 
- target - The target element selector. 

