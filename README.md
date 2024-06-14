I have created a GitHub homepage where I will provide a brief introduction about myself and showcase my code in the future.

![Image](https://github.com/users/vancyland/projects/1/assets/127710303/70f74ee3-ec0f-488a-a8ca-1855f50eea5c)

下面视频是animatediff v3根据上图作为ref图像生成的视频,可以发现，生成的视频一致性不佳，如图红色框内，船帆变为几段

<div align="center">
  <img src="https://github.com/users/vancyland/projects/1/assets/127710303/7582daea-9214-4193-9e40-a7691c5e05f9" width="30%"/>
  <img src="https://github.com/users/vancyland/projects/1/assets/127710303/7c06b544-c669-481c-9aea-75dd85ed0689" width="30%"/>
  <img src="https://github.com/users/vancyland/projects/1/assets/127710303/a2dca508-d084-4451-9e2a-b25d82344073" width="30%"/>
</div>

在所有timesteps加入SparseCausalAttention/第一帧/平均帧信息到所有upblock的SA后，分别生成以下三个视频.可以看出，一致性确实提升，但是生成视频质量下降，motion信息丢失?

<div align="center">
  <img src="https://github.com/users/vancyland/projects/1/assets/127710303/d51b43b5-9a86-42e4-b971-f9f5e4415f54" width="30%"/>
  <img src="https://github.com/users/vancyland/projects/1/assets/127710303/4028b16c-117e-481d-aceb-7edb6722fd0e" width="30%"/>
  <img src="https://github.com/users/vancyland/projects/1/assets/127710303/1c5c79b0-bb3e-4547-a166-87edc57b260b" width="30%"/>
</div>

进一步对timesteps[1-25]进行消融，即对timestep>[0,4,5]的情况下注入第一帧/平均帧信息到SA后得到

<table>
  <tr>
    <td align="center">
      <p>0</p>
      <img src="https://github.com/vancyland/vancyland.github.io/assets/127710303/076cf87d-a193-404b-bd2e-451ba48b2874" width="100%">
    </td>
    <td align="center">
      <p>4</p>
      <img src="https://github.com/vancyland/vancyland.github.io/assets/127710303/a153ee1c-2688-442d-bad9-dd1645adcc7e" width="100%">
    </td>
    <td align="center">
      <p>5</p>
      <img src="https://github.com/vancyland/vancyland.github.io/assets/127710303/e52309a8-4f7a-4f43-8132-e6cf1b3e3d62" width="100%">
    </td>
  </tr>
  <tr>
    <td align="center">
      <p></p>
      <img src="https://github.com/vancyland/vancyland.github.io/assets/127710303/7443ea6f-dfb0-404a-ac77-c71309415445" width="100%">
    </td>
    <td align="center">
      <p></p>
      <img src="https://github.com/vancyland/vancyland.github.io/assets/127710303/cfdac4a6-d039-49a5-9c19-6dcefb9b3c44" width="100%">
    </td>
    <td align="center">
      <p></p>
      <img src="https://github.com/vancyland/vancyland.github.io/assets/127710303/b3f4faa9-0ea3-43f7-b4c3-3c33ecf8df9a" width="100%">
    </td>
  </tr>
</table>










