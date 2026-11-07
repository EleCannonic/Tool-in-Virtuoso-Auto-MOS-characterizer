将本目录中的文件 mc（不是整个目录）复制到 ~/ic/mc。
将压缩包中的 mos_characterizer 目录安装到 ~/ic/mos_characterizer。
从 ~/ic 启动 Virtuoso 后，在 CIW 输入 load("mc")。
mc 是加载脚本文件，mc/ 是压缩包里的分发目录。不要将 ~/ic/mc 安装成文件夹。
不修改 .cdsinit 或任何启动文件。从其他工作目录启动时，请使用 load("~/ic/mc")，或先切换工作目录。
