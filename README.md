<div align="center">

## donwload script


</div>

### Description

Do not open in inline browser but offer to download or open the file.
 
### More Info
 
download.php?fileName=bla.pdf

-only the "$allowed" types will be possible to download.

- no back reference is possible. like ../ or ./

open - save bla.pdf


<span>             |<span>
---                |---
**Submitted On**   |
**By**             |[the\_firm](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByAuthor/the-firm.md)
**Level**          |Advanced
**User Rating**    |4.7 (14 globes from 3 users)
**Compatibility**  |PHP 4\.0
**Category**       |[Files](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByCategory/files__8-2.md)
**World**          |[PHP](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByWorld/php.md)
**Archive File**   |[](https://github.com/Planet-Source-Code/the-firm-donwload-script__8-1833/archive/master.zip)

### API Declarations

@the_firm


### Source Code

```
<?php
	preg_match("/^(.*[\/])*(.+).(php|php3)$/i", $_SERVER["SCRIPT_FILENAME"], $basedir);
	$fileName = $_GET["fileName"];
	if(!empty($fileName)) {
		$allowed = "pdf|doc|xls|ppt|jpg|jpeg|png|gif|zip|rar";
		preg_match("/^([0-9a-z_]+[\/])*([0-9a-z_]+).(".$allowed.")$/i", $fileName, $file);
		if(sizeof($file) == 4) {
			if (file_exists($basedir[1] . $file[0]) && is_file($basedir[1] . $file[0])) {
				$contentLength = filesize($file[0]);
				$m_fileName = $file[2] . "." . $file[3];
				Header ("Content-Type: application/octet-stream; name=" . $m_fileName);
				Header ("Content-Length: " . $contentLength);
				Header ("Content-Disposition: attachment; filename=" . $m_fileName);
				readfile($file[0]);
			} else {
				echo "<b>This file does not exist!</b>";
			}
		} else {
			echo "<b>This file does not exist or filetype is not allowed to download!</b>";
		}
	} else {
		echo "<b>No file selected...</b>";
	}
?>
```

