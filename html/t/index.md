# tcctcc

<!--more-->
<!DOCTYPE html>
<html lang="zh">

<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width,user-scalable=no" />
  <title>3D Carousel</title>
  <link type="text/css" rel="styleSheet"  href="3d-carousel.css" />
</head>

<body>
  <div id="drag-container">
    <div id="spin-container">

      <!-- Add your images (or video) here -->
      <img src="1.jpg" alt="田婵婵" />
      <img src="2.jpg"/>
      <img src="3.jpg" />
      <img src="4.jpg" />
      <img src="5.jpg" />
      
      <img src="5.jpg" alt="田婵婵" />
      <img src="4.jpg"/>
      <img src="3.jpg" />
      <img src="2.jpg" />
      <img src="1.jpg" />

      <!-- Example image with link -->
      <a target="_blank" href="4.jpg">
        <img src="4.jpg" alt="" title="田婵婵" />
      </a>
      <a target="_blank" href="4.jpg">
        <img src="4.jpg" alt="" title="田婵婵" />
      </a>

      <!-- Example add video  -->
      <video controls autoplay="autoplay" loop title="mv-刘德华-今天">
        <source src="/video/7144295491784707358.mp4" type="video/mp4" />
      </video>

      <!-- Text at center of ground -->
      <p style="width:100px;">田婵婵-3D</p>
    </div>
    <div id="ground"></div>
  </div>

  <div id="music-container"></div>
  <script>
    // Author: Hoang Tran (https://www.facebook.com/profile.php?id=100004848287494)
    // Github verson (1 file .html): https://github.com/HoangTran0410/3DCarousel/blob/master/index.html

    // You can change global variables here:
    var radius = 240; // how big of the radius
    var autoRotate = true; // auto rotate or not
    var rotateSpeed = -60; // unit: seconds/360 degrees
    var imgWidth = 120; // width of images (unit: px)
    var imgHeight = 170; // height of images (unit: px)

    // Link of background music - set 'null' if you dont want to play background music
    var bgMusicURL = "";
    var bgMusicControls = true; // Show UI music control

    /*
   NOTE:
     + imgWidth, imgHeight will work for video
     + if imgWidth, imgHeight too small, play/pause button in <video> will be hidden
     + Music link are taken from: https://hoangtran0410.github.io/Visualyze-design-your-own-/?theme=HauMaster&playlist=1&song=1&background=28
     + Custom from code in tiktok video  https://www.facebook.com/J2TEAM.ManhTuan/videos/1353367338135935/
    */

    // ===================== start =======================
    setTimeout(init, 100);

    var odrag = document.getElementById("drag-container");
    var ospin = document.getElementById("spin-container");
    var aImg = ospin.getElementsByTagName("img");
    var aVid = ospin.getElementsByTagName("video");
    var aEle = [...aImg, ...aVid]; // combine 2 arrays

    // Size of images
    ospin.style.width = imgWidth + "px";
    ospin.style.height = imgHeight + "px";

    // Size of ground - depend on radius
    var ground = document.getElementById("ground");
    ground.style.width = radius * 3 + "px";
    ground.style.height = radius * 3 + "px";

    function init(delayTime) {
      for (var i = 0; i < aEle.length; i++) {
        aEle[i].style.transform =
          "rotateY(" +
          i * (360 / aEle.length) +
          "deg) translateZ(" +
          radius +
          "px)";
        aEle[i].style.transition = "transform 1s";
        aEle[i].style.transitionDelay =
          delayTime || (aEle.length - i) / 4 + "s";
      }
    }

    function applyTranform(obj) {
      // Constrain the angle of camera (between 0 and 180)
      if (tY > 180) tY = 180;
      if (tY < 0) tY = 0;

      // Apply the angle
      obj.style.transform = "rotateX(" + -tY + "deg) rotateY(" + tX + "deg)";
    }

    function playSpin(yes) {
      ospin.style.animationPlayState = yes ? "running" : "paused";
    }

    var sX,
      sY,
      nX,
      nY,
      desX = 0,
      desY = 0,
      tX = 0,
      tY = 10;

    // auto spin
    if (autoRotate) {
      var animationName = rotateSpeed > 0 ? "spin" : "spinRevert";
      ospin.style.animation = `${animationName} ${Math.abs(
        rotateSpeed
      )}s infinite linear`;
    }

    // add background music
    if (bgMusicURL) {
      document.getElementById("music-container").innerHTML +=
        '<audio src="${bgMusicURL}" ${bgMusicControls ? "controls" : ""} autoplay loop>' +
        "<p>If you are reading this, it is because your browser does not support the audio element.</p>" +
        "</audio>";
    }

    // setup events
    document.onpointerdown = function (e) {
      clearInterval(odrag.timer);
      e = e || window.event;
      var sX = e.clientX,
        sY = e.clientY;

      this.onpointermove = function (e) {
        e = e || window.event;
        var nX = e.clientX,
          nY = e.clientY;
        desX = nX - sX;
        desY = nY - sY;
        tX += desX * 0.1;
        tY += desY * 0.1;
        applyTranform(odrag);
        sX = nX;
        sY = nY;
      };

      this.onpointerup = function (e) {
        odrag.timer = setInterval(function () {
          desX *= 0.95;
          desY *= 0.95;
          tX += desX * 0.1;
          tY += desY * 0.1;
          applyTranform(odrag);
          playSpin(false);
          if (Math.abs(desX) < 0.5 && Math.abs(desY) < 0.5) {
            clearInterval(odrag.timer);
            playSpin(true);
          }
        }, 17);
        this.onpointermove = this.onpointerup = null;
      };

      return false;
    };

    document.onmousewheel = function (e) {
      e = e || window.event;
      var d = e.wheelDelta / 20 || -e.detail;
      radius += d;
      init(1);
    };
  </script>
</body>

</html>

---

> 作者: [geekswg](https://geekswg.github.io)  
> URL: https://geekswg.github.io/html/t/  

