文件夹：
raw_p1-6_pictures：第一条到第七条焊道的原始截面，（每0.4mm截取一张，网格大小为0.4mm）
cropped_binary_resized_mirror：对p1-7_pictures，截取基材部分
cropped_binary_resized_mirror_minisize：再次截取焊缝部分，减小尺寸，用于作为模型输入
p2-7_extracted_cropped_binary：对cropped_binary_resized_mirror中不同焊道数据相减，得到单个焊道像素（焊道2 3 4 5 6 7）
fitted_extraceed：对p2-7_extracted_cropped_binary的单个焊道数据拟合，得到拟合圆的位置、半径(像素位置)

程序：
trajectory.ipynb：走斜线的轨迹，0.4mm截取一个焊接点，作为输入的焊接位置向量（每条焊道截取280张图片，先只用前面200张图片，焊接位置也选择前200个轨迹点）


p1-6_predict.txt：数据集，输入图片、焊接位置x、焊接位置y、拟合位置x、拟合位置y、拟合半径r（均是像素大小，坐标系为cropped_binary_resized_mirror_minisize图片像素坐标系）