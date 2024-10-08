![Image](https://github.com/users/vancyland/projects/1/assets/127710303/70f74ee3-ec0f-488a-a8ca-1855f50eea5c)

The following video is generated by animatediff v3 using the above image as the reference. It can be observed that the consistency of the generated video is poor; for example, within the red box in the image, the sail of the boat has turned into several segments.

<div align="center">
  <img src="https://github.com/users/vancyland/projects/1/assets/127710303/7582daea-9214-4193-9e40-a7691c5e05f9" width="30%"/>
  <img src="https://github.com/users/vancyland/projects/1/assets/127710303/7c06b544-c669-481c-9aea-75dd85ed0689" width="30%"/>
  <img src="https://github.com/users/vancyland/projects/1/assets/127710303/a2dca508-d084-4451-9e2a-b25d82344073" width="30%"/>
</div>

Introducing popular methods to enhance video generation consistency, specifically the cross-frame attention mechanism.

In particular, by adding SparseCausal Attention, the first frame, and averaged frame information to the SA of all upblocks across all timesteps, we generate the following three videos.

It can be observed that while consistency has indeed improved, the quality of the generated videos has decreased, potentially resulting in a loss of motion information.

<div align="center">
  <img src="https://github.com/users/vancyland/projects/1/assets/127710303/d51b43b5-9a86-42e4-b971-f9f5e4415f54" width="30%"/>
  <img src="https://github.com/users/vancyland/projects/1/assets/127710303/4028b16c-117e-481d-aceb-7edb6722fd0e" width="30%"/>
  <img src="https://github.com/users/vancyland/projects/1/assets/127710303/1c5c79b0-bb3e-4547-a166-87edc57b260b" width="30%"/>
</div>

To further analyze, we conduct an ablation study on timesteps and upblocks.

Ablation of timesteps [1-25]: For the case where timesteps are greater than [0, 4, 5], we inject the first frame and averaged frame information into the SA, resulting in the following outcomes.

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

Ablation of upblocks 1, 2, and 3: We separately inject the first frame and averaged frame information into the SA of upblocks 1, 2, and 3. The results of this approach are as follows.


     
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




