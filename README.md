# 构建智能共生——OpenAI 的人工智能技术简介
# OpenAI-interactive-animation


这是一个模仿老版本的OpenAI官网做的交互动画例子，也是我交互动画课程的大作业
This is an interactive animation example imitating the old version of OpenAI official website, and it is also a big assignment for my interactive animation course.


## 一、作品名称及简介

这部交互动画作品名称为《构建智能共生——OpenAI 的人工智能技术简介》，主要展示OpenAI的核心技术，详细讲述GPT模型以及如何将这一技术应用于实际场景。使用户将不仅了解高精准度的文本生成模型，还能了解到OpenAI在语音识别、计算机视觉和自然语言处理等领域的发展，体验到OpenAI致力于推动人工智能技术与人类共生发展的愿景。

## 二、作品框架图

![image](https://github.com/user-attachments/assets/4bdb45f5-2750-4f95-8392-bb5137ad22ee)

## 三、作品创新点

本作品采用基于交互的动画设计，在动画设计上，我们多样的效果和技巧，包括渐入渐出动画、逐帧动画、连续、手势动效、轮播图动画效果等。  
本作品采用简洁明了的UI设计风格，采用黑色作为主要背景色，选择了能够代表着科技、未来和创新的青色作为主要色调，运用方框和扁平化元素进行搭配，用白色字体突出文字内容，用不同尺寸的字体来区分不同层级的信息内容。  
本作品通过交互动画的形式展示人工智能。通过演示自然语言处理、生成模型或图像等可视化演示，展现OpenAI 的各种功能，让用户更加直观地了解人工智能的应用。并且，作品中通过与用户交互，详细展示了如何使用GPT，帮助用户理解如何使用人工智能来帮助完成各种任务。

## 四、作品的实现过程描述

1. 实现逐帧动画，展现打字机效果：

    ```javascript
    var element = document.getElementById('gpt4');
    var paragraphs = element.getElementsByTagName('p');
    var lines = [];

    for (var i = 0; i < paragraphs.length; i++) {
      var line = paragraphs[i].textContent.trim();
      lines.push(line);
      paragraphs[i].innerHTML = '';
    }

    function typewriterEffect(lineIndex, charIndex) {
      if (lineIndex >= lines.length) return;
      var line = lines[lineIndex];
      var timer = setInterval(function() {
        paragraphs[lineIndex].innerHTML += line.charAt(charIndex);
        charIndex++;
        if (charIndex >= line.length) {
          clearInterval(timer);
          paragraphs[lineIndex].innerHTML += '<br>';
          typewriterEffect(lineIndex + 1, 0);
        }
      }, 30);
    }
    element.style.color = '#FFFFFF';
    typewriterEffect(0, 0);
    ```

2. 实现轮播图的动画效果：

    ```javascript
    var index = 1;
    var prevBtn = document.getElementById('prevBtn');
    var nextBtn = document.getElementById('nextBtn');
    var imageIds = ["img1", "img2", "img3"];

    prevBtn.addEventListener('click', function() {
      index--;
      if (index === 0) {
        index = 3;
      }
      for (var i = 0; i < imageIds.length; i++) {
        var imageId = imageIds[i];
        var image = document.getElementById(imageId);
        image.style.display = 'none';
      }
      var image = document.getElementById('img' + index);
      image.style.display = 'block';
    });

    nextBtn.addEventListener('click', function() {
      index++;
      if (index === 4) {
        index = 1;
      }
      for (var i = 0; i < imageIds.length; i++) {
        var imageId = imageIds[i];
        var image = document.getElementById(imageId);
        image.style.display = 'none';
      }
      var image = document.getElementById('img' + index);
      image.style.display = 'block';
    });
    ```

3. 为控制页面展示的流程，通过控制元素的样式属性，实现了内容的切换、隐藏和显示。

    ```javascript
    firstText.style.display = 'none';
    secondText.style.display = 'inline';
    prevButton.style.display = 'inline';
    nextButton.style.display = 'none';
    element.style.display = 'none';
    element2.style.display = 'inline';
    ```

体会：  
制作以上效果过程中，主要涉及到JavaScript对HTML文档的操作和控制，需要熟悉常用的DOM操作方法和CSS样式属性。总的来说，交互动画的制作需要考虑多种因素，如页面设计、用户需求、技术实现等，需要灵活运用不同的技术手段，提高页面的交互性和吸引力，让用户获得更好的体验。

## 五、关键部分截图

1. 实现打字机的动画效果：

    ![image](https://github.com/user-attachments/assets/6c722a54-c296-4c34-8ce1-aee5dea6a32c)

2. 通过轮播图来展示DALL·E 2可以对来自自然语言的现有图像进行编辑，说明文字它可以添加和删除元素拍摄阴影、反射和纹理的功能。

    ![image](https://github.com/user-attachments/assets/e4a53e70-eb3a-4553-957b-9fc966d8aeda)
    ![image](https://github.com/user-attachments/assets/5b6a4d6d-29fb-4918-8df7-571195c03db7)

3. 实现了演示功能。点击发送后，左边的历史记录栏，会多一个信息，且将之前的信息都往下移动。做了个关键帧动画，并且做出了等gpt头像渐隐出来后运行打字机效果，和实现了点击response后会出现两个信息，做出了点击向左文字变换和箭头隐藏等小细节。

    ![image](https://github.com/user-attachments/assets/40618183-df6b-4aa0-b7c4-e6477b81da57)
    ![image](https://github.com/user-attachments/assets/107dafa1-496b-49b2-839b-949e823f37f0)
