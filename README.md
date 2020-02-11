# Apple 홈페이지 똑같이 만들기
유투버 1분코딩 님의 교육영상에서 제공되는 코드를 리팩토링하고, 직접 만들어 학습하기 위해 작성

## 제작/교육 영상
[애플 웹사이트 iPhone X 비주얼 똑같이 만들기 #1](https://www.youtube.com/watch?v=pLaON5_bysU)

## Demo
[Demo](https://studiomeal.com/data/code/sample/iphonex/)

# 설명
코드를 이해하는데 도움이 될만한 설명 정리.

## Scroll, Resize event
스크롤이 변경됨에 따라서 위치에 따라 Canvas 를 다시 그리도록 한다.
```javascript
window.addEventListener('resize', function () {
  requestAnimationFrame(resizeHandler);
});
window.addEventListener('scroll', function () {
  requestAnimationFrame(scrollHandler);
});
```

## Keyframe
실제 데모를 보다보면, 스크롤이 중간쯤에서 속도의 변화를 느낄 수 있는데, 이를 위해 keyframe 을 2개로 나누어
따로 처리할 수 있도록 한다.
```javascript
render = function () {
  // ...
  var videoScale, triangleMove, rectangleMove;
  if (keyframes[currentKeyframe]) {
      videoScale = calcAnimationValue(keyframes[currentKeyframe].animationValues.videoScale);
      triangleMove = calcAnimationValue(keyframes[currentKeyframe].animationValues.triangleMove);
      rectangleMove = calcAnimationValue(keyframes[currentKeyframe].animationValues.rectangleMove);
  } else {
    return;
  }  
  // ...
}

```

## Canvas size
Canvas 의 width, height, style width, style height 를 설정하는 부분이다.
```javascript
elemCanvas.width = canvasWidth = windowWidth * 2;
elemCanvas.height = canvasHeight = windowHeight * 2;
elemCanvas.style.width = windowWidth + 'px';
elemCanvas.style.height = windowHeight + 'px';
```
Canvas 의 크기를 늘인 후, 실제 크기에 맞게 축소시키면 더 선명하게 보이도록 할 수 있다.
