Whisper by OpenAI - Install and Export Text Script
>> 安裝Python最新版本:

 
Check the Box of "Add Pyhton.exe to PATH"

>> 安裝Pytorch :


Copy Command to CMD.

>>安裝 Chocolatey :

選擇Individual

Copy the Command.

Open Window PowerShell Run as administrator.

Paste Command

After Installing Chocolatey, install ffmpeg.



choco install ffmpeg

then , press "Y"

>> Install Whisper :

pip install -U openai-whisper

如果有 NVIDIA GPU，安装 CUDA 版以加速处理（可选）：

pip install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu118

============================================

在MP4 Directory 下，Address 輸入cmd.

whisper outputVideo.mp4 --model medium --language Japanese --outputformat txt



如mp4名稱有空格，則加上double quote >> "Output Video.mp4"

**尝试更大的模型（如 large），或确保音频质量（减少背景噪音）。可以用 Audacity 清理音频。

%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%

>>批量处理：如果有多个 MP4 文件，可以编写脚本批量提取音频和转录。示例（Python）：

import os

import subprocess

for mp4_file in os.listdir('.'):

    if mp4_file.endswith('.mp4'):

        audiofile = mp4file.replace('.mp4', '.mp3')

        subprocess.run(['ffmpeg', '-i', mp4file, '-vn', '-acodec', 'mp3', audiofile])

        subprocess.run(['whisper', audiofile, '--model', 'medium', '--language', 'Japanese', '--outputformat', 'txt'])

%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%

>>如遇上whisper 未安裝妥當:

打开命令行（Windows CMD、PowerShell 或终端），运行：

pip show openai-whisper

如果 Whisper 已安装，你会看到类似以下输出：

Name: openai-whisper

Version: x.x.x

Location: C:\Users\YourUser\AppData\Local\Programs\Python\Python313\Lib\site-packages

...

检查 Python Scripts 目录是否在 PATH 中:

Whisper 的命令行工具通常安装在 Python 的 Scripts 目录（例如 C:\Users\YourUser\AppData\Local\Programs\Python\PythonXX\Scripts）。

验证 Scripts 目录： 

运行以下命令，检查 Whisper 可执行文件是否存在：

C:\Users\YourUser\AppData\Local\Programs\Python\PythonXX\Scripts\whisper.exe

添加 Scripts 目录到 PATH：

Windows： 

搜索“环境变量”并打开“Edit Environment System Variables"。

在“系统变量”中找到 Path，点击“编辑”。

添加 Python 的 Scripts 目录，例如：

C:\Users\YourUser\AppData\Local\Programs\Python\PythonXX\Scripts


✦✦✦✦✦✦✦✦✦✦✦✦✦✦✦✦✦✦✦✦✦✦✦✦✦✦✦✦✦✦✦✦✦✦✦✦✦✦✦✦✦✦✦✦✦✦

>>使用 Python 模块运行 Whisper

如果直接运行 whisper 命令仍不生效，可以通过 Python 模块直接调用：

python -m whisper outputaudio.mp3 --model medium --language Japanese --outputformat txt


✦✦✦✦✦✦✦✦✦✦✦✦✦✦✦✦✦✦✦✦✦✦✦✦✦✦✦✦✦✦✦✦✦✦✦✦✦✦✦✦✦✦✦✦✦✦
