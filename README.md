I have created a GitHub homepage where I will provide a brief introduction about myself and showcase my code in the future.

![Image](https://github.com/users/vancyland/projects/1/assets/127710303/70f74ee3-ec0f-488a-a8ca-1855f50eea5c)

下面视频是animatediff v3根据上图作为ref图像生成的视频

![Image](https://github.com/users/vancyland/projects/1/assets/127710303/7582daea-9214-4193-9e40-a7691c5e05f9)

可以发现，生成的视频一致性不佳，如图红色框内，船帆变为几段

<div align="center">
  <img src="https://github.com/users/vancyland/projects/1/assets/127710303/7c06b544-c669-481c-9aea-75dd85ed0689" width="45%"/>
  <img src="https://github.com/users/vancyland/projects/1/assets/127710303/a2dca508-d084-4451-9e2a-b25d82344073" width="45%"/>
</div>

加入SparseCausalAttention/第一帧/平均帧信息到SA后，分别变为

<div align="center">
  <img src="https://github.com/users/vancyland/projects/1/assets/127710303/d51b43b5-9a86-42e4-b971-f9f5e4415f54" width="30%"/>
  <img src="https://github.com/users/vancyland/projects/1/assets/127710303/4028b16c-117e-481d-aceb-7edb6722fd0e" width="30%"/>
  <img src="https://github.com/users/vancyland/projects/1/assets/127710303/1c5c79b0-bb3e-4547-a166-87edc57b260b" width="30%"/>
</div>

一致性确实提升，但是生成视频质量下降同时motion信息丢失。











