# Arc Model Project

该项目旨在使用Python进行焊缝截面图像的批量裁剪、二值化处理以及焊道轮廓的提取及拟合。

## Requirements

- Python 3.x
- numpy
- Pillow (PIL)
- scipy

## Notebook Usage and Description

先将待处理的图像放置在适当的文件夹中，随后运行`*.ipynb` notebook执行以下步骤：

1. 导入必要的库。
2. 遍历包含图像的指定文件夹。
3. `crop_1st.ipynb`: 从软件导出截面图片到工件部分的提取及二值化。
4. `crop_2nd.ipynb`: 从完整工件部分到焊缝部分的裁剪。
5. `extract.ipynb`: 提取焊道像素。
6. `fitting.ipynb`: 拟合焊道轮廓。
7. 将处理后的图像保存到输出目录。
8. `classify.ipynb`: 不同x位置下的截面图片分类。

## Directory Structure

```
curve_fitting_slope/
├── cropped_binary_resized_mirror/
│   ├── cropped_binary_resized_mirror_p1/
│   ├── cropped_binary_resized_mirror_p2/
│   └── ...
├── cropped_binary_resized_mirror_minisize/
│   ├── cropped_binary_resized_mirror_minisize_p1/
│   ├── cropped_binary_resized_mirror_minisize_p2/
│   └── ...
├── crop_cv2_2rd.ipynb
└── README.md
```

## Folders

- **raw_p1-6_pictures**: 第一条到第七条焊道的原始截面，（每0.4mm截取一张，网格大小为0.4mm）。
- **cropped_binary_resized_mirror**: 对 `p1-7_pictures`，截取基材部分。
- **cropped_binary_resized_mirror_minisize**: 再次截取焊缝部分，减小尺寸，用于作为模型输入。
- **p2-7_extracted_cropped_binary**: 对 `cropped_binary_resized_mirror` 中不同焊道数据相减，得到单个焊道像素（焊道2 3 4 5 6 7）。
- **fitted_extraceed**: 对 `p2-7_extracted_cropped_binary` 的单个焊道数据拟合，得到拟合圆的位置、半径(像素位置)。
- **classify**: 不同x位置下的截面图片。

## Program

- `trajectory.ipynb`: 走斜线的轨迹，0.4mm截取一个焊接点，作为输入的焊接位置向量（每条焊道截取280张图片，先只用前面200张图片，焊接位置也选择前200个轨迹点）。

## Dataset

- **Data**: 完整工件图片数据集。
- **Data_minisize**: 焊缝部分图片数据集。
- **labels-240301-p1_p6.txt**: 数据集，输入图片、焊接位置x、焊接位置y、拟合位置x、拟合位置y、拟合半径r（均是像素大小，坐标系为 `cropped_binary_resized_mirror` 图片像素坐标系，要得到 `cropped_binary_resized_mirror_minisize` 图片像素坐标系下的位置坐标，参考**crop_2nd**里裁剪框设置）。
- **error.txt**: 拟合误差。
- **pridict.txt**: 拟合圆的信息（应该是位置(x, y)）。

## License

该项目使用MIT License许可。
