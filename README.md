I have created a GitHub homepage where I will provide a brief introduction about myself and showcase my code in the future.

![Image](https://github.com/users/vancyland/projects/1/assets/127710303/70f74ee3-ec0f-488a-a8ca-1855f50eea5c)

下面视频是animatediff v3根据上图作为ref图像生成的视频,可以发现，生成的视频一致性不佳，如图红色框内，船帆变为几段

<div align="center">
  <img src="https://github.com/users/vancyland/projects/1/assets/127710303/7582daea-9214-4193-9e40-a7691c5e05f9" width="30%"/>
  <img src="https://github.com/users/vancyland/projects/1/assets/127710303/7c06b544-c669-481c-9aea-75dd85ed0689" width="30%"/>
  <img src="https://github.com/users/vancyland/projects/1/assets/127710303/a2dca508-d084-4451-9e2a-b25d82344073" width="30%"/>
</div>

引入popular增强视频生成一致性的做法，跨帧注意力机制。
具体而言在所有timesteps加入SparseCausalAttention/第一帧/平均帧信息到所有upblock的SA后，分别生成以下三个视频.
可以看出，一致性确实提升，但是生成视频质量下降，motion信息丢失?

<div align="center">
  <img src="https://github.com/users/vancyland/projects/1/assets/127710303/d51b43b5-9a86-42e4-b971-f9f5e4415f54" width="30%"/>
  <img src="https://github.com/users/vancyland/projects/1/assets/127710303/4028b16c-117e-481d-aceb-7edb6722fd0e" width="30%"/>
  <img src="https://github.com/users/vancyland/projects/1/assets/127710303/1c5c79b0-bb3e-4547-a166-87edc57b260b" width="30%"/>
</div>

为进一步分析，对timestep和upblock进行消融探讨

1.timesteps[1-25]消融，对timestep>[0,4,5]的情况下注入第一帧/平均帧信息到SA后得到

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

2.upblock.1/2/3消融，分别只注入第一帧/平均帧信息到upblock.1/2/3的SA中

     
<div align="center">
 <img src="https://github.com/vancyland/vancyland.github.io/assets/127710303/0358d882-01f3-4eb4-8192-f2a25b1d43aa" width="30%">
</div>
  以上
  
<table>
  <tr>
    <td align="center">
      <p>upblock.123</p>
      <img src="https://github.com/vancyland/vancyland.github.io/assets/127710303/2bb37eec-4ead-400d-b973-cc81bd076121" width="100%">
    </td>
    <td align="center">
      <p>upblock.1</p>
      <img src="https://github.com/vancyland/vancyland.github.io/assets/127710303/5fe4dd1b-d8cf-4bc3-84fc-994f8a763a8f" width="100%">
    </td>
    <td align="center">
      <p>upblock.2</p>
      <img src="https://github.com/vancyland/vancyland.github.io/assets/127710303/d8b28a49-8de6-45fd-82df-d17287a1d30d" width="100%">
    </td>
    <td align="center">
      <p>upblock.3</p>
      <img src="https://github.com/vancyland/vancyland.github.io/assets/127710303/0890e045-d2c1-4ffc-adb9-3deed69a8378" width="100%">
    </td>
    <td align="center">
      <p>None</p>
      <img src="https://github.com/vancyland/vancyland.github.io/assets/127710303/2f9a8790-8b36-451f-90dd-37a814b4121d" width="100%">
    </td>
  </tr>
  <tr>
    <td align="center">
      <p></p>
      <img src="https://github.com/vancyland/vancyland.github.io/assets/127710303/6c2a0891-b84a-4772-8e99-6ba566134513" width="100%">
    </td>
    <td align="center">
      <p></p>
      <img src="https://github.com/vancyland/vancyland.github.io/assets/127710303/f7942f19-b906-49aa-838a-3b4d0fa95459" width="100%">
    </td>
    <td align="center">
      <p></p>
      <img src="https://github.com/vancyland/vancyland.github.io/assets/127710303/20c22a28-6369-4177-9ddf-db0101190f39" width="100%">
    </td>
    <td align="center">
      <p></p>
      <img src="https://github.com/vancyland/vancyland.github.io/assets/127710303/1b4d4881-75b3-46d2-9c87-7e00915499ef" width="100%">
    </td>
    <td align="center">
      <p></p>
      <img src="https://github.com/vancyland/vancyland.github.io/assets/127710303/87b15f18-3f9c-4327-91d1-895afc46423b" width="100%">
    </td>
  </tr>
</table>

综合考虑视频质量和一致性，采用平均帧


<table>
 <tr>
    <td align="center">
      <p></p>
      <img src="https://github.com/vancyland/vancyland.github.io/assets/127710303/d4910803-0bd7-4149-b9b1-91e3aaadde6e" width="100%">
    </td>
   </tr>
  <tr>
    <td align="center">
      <p></p>
      <img src="https://github.com/vancyland/vancyland.github.io/assets/127710303/ad49313d-f98a-479e-9965-2ef5f8c1011f" width="100%">
    </td>
    </tr>
  <tr>
    <td align="center">
      <p></p>
      <img src="https://github.com/vancyland/vancyland.github.io/assets/127710303/ef916be8-b377-42b8-8898-bf1ff3221701" width="100%">
    </td>
    </tr>
  <tr>
    <td align="center">
      <!-- Placeholder for empty cell -->
    </td>
  </tr>
</table>

