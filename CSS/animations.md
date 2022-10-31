# Animations 
- Animations consist of two components - a style describing the CSS animation and a set of keyframes that indicate the start and end states of the animation's style as well as possible intermediate waypoints.
- There are three key advantages to CSS animations over traditional script-driven animation -
  - Easy to use for simple animations; can be create without JS. 
  - They run well, even under moderate system load. 
  - Letting the browser control animation sequence lets the browser optimise performance and efficiency. 

## Configuring an Animation 
- To create a CSS animation sequence, you style the element you want to animate with the animation property or its sub-properties. This lets you configure the timing, duration and other details of how the animation sequence should progress. 
- This doesn't configure the actual apperance of the animation, which is done using the @keyframes at-rule. 

## Defining animation sequence using keyframes
- After you've configured the animation's timing, you need to define the appearance of the animation. This is done by establishing one or more keygrames using the @keyframes at-rule. Each keyframe describes how the animated element should render at a given time during the animation sequence.
- Since the timing of the animation is defined in the CSS style that configures the animation, keyframes use a percentage to indicate the time during the animation sequence at which they take place. 
- 0% indicates the first moment of the animation sequence, while 100% indicates the final state of the animation. Because these two times are so important, they have special aliases: `from` and `to`. Both optional. 
- If `from/0%` or `to/100%` isnot specifed, the broswer starts or finishes the animation using the computed values of all attributes. 

```
p {
  animation-duration: 3s;
  animation-name: slidein;
  animation-iteration-count: infinite;
}
```

```
@keyframes slidein {
  from {
    margin-left: 100%;
    width: 300%;
  }

  to {
    margin-left: 0%;
    width: 100%;
  }
}
```
