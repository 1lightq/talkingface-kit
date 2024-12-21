# 使用Python 3.9镜像作为基础镜像
FROM python:3.9-slim

# 设置工作目录
WORKDIR /app/code

# 将本地项目文件复制到容器中

COPY . /app
COPY requirements.txt /app/requirements.txt

# 安装项目所需的依赖
RUN apt-get update && apt-get install -y build-essential cmake python3-dev gcc g++ libatlas-base-dev
RUN pip install --no-cache-dir -r /app/requirements.txt

# 容器启动时运行的命令（如果有）
CMD ["python", "demo.py", "--infer_type", "mfcc_pose_only", "--stage1_checkpoint_path", "./ckpts/stage1.ckpt", "--stage2_checkpoint_path", "./ckpts/stage2_pose_only_mfcc.ckpt", "--test_image_path", "./test_demos/portraits/Monalisa.jpg", "--test_audio_path", "./test_demos/audios/Monalisa.wav", "--result_path", "./outputs/monalisa_mfcc", "--control_flag", "--seed", "0", "--pose_yaw", "0.25", "--pose_pitch", "0", "--pose_roll", "0"]

