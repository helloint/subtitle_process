# 给英语视频添加双语字幕的一个解决方案
## 命令说明
### 导出 (Extract)
npm环境`npm run extract`, 或者node环境, `node extract.js`, 字幕文件会提取到 translation.txt  
### 合并 (Merge)
npm环境`npm run merge`, 或者node环境, `node merge.js`, 翻译文件 translated.txt 会被追加到已有的英文字幕后(换行显示)  
### 生成字幕文件 (Srt)
npm环境`npm run srt`, 或者node环境, `node srt.js`, 导出srt字幕文件  

## How To Use
### 准备
0. 环境配置：  
安装【node/npm环境】  
安装【剪映[桌面端](https://lv.ulikecam.com/)】  
安装【[FFmpeg](http://ffmpeg.org/download.html)】    
1. 在剪映里导入原视频，通过剪映自动生成英语字幕(菜单/文本/识别字幕)。退出剪映。
2. 把剪映草稿的配置文件($Users\AppData\Local\JianyingPro\User Data\Projects\com.lveditor.draft)`draft_content.json`复制到当前目录，运行【导出】待翻译文件 `translation.txt`
3. 用 Google Translation 翻译 `translation.txt`，得到 `translated.txt`。 注意比对行数，确保内容不要错位。
4. 运行【导入】 合并成 `draft_content_imported.json`。
4. 运行【生成字幕文件】 生成 `subtitle.srt`。
6. 通过FFmpeg合成字幕，同时压缩视频。  
`ffmpeg -y -i src.mp4 -lavfi "subtitles=subtitle.srt" -c:v h264 -rc constqp -qp 25 dist.mp4`
