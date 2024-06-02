---
'@lottiefiles/lottie-interactivity': patch
---

Enforce player to render the edging action frame during scroll with action.type = "seek".

Currently, during fast scrolling, the player may not render the very last or first frame of the provided action range.

Example:
```
action: {
  visibility: [0.2, 0.8],
  type: "seek",
  frames: [0, 100]
}
```

When scrolling down, if at some point the container visibility is 0.72 and on the next scroll event it becomes 0.81, the
current behavior stops the player at the frame corresponding to 0.72. For certain animations, this is crucial: if the
container has passed its bottom visibility point, it should be stopped on the very last frame of the range.

This fix addresses this issue.
