
### log( str )
文字列をデベロッパーコンソールに表示し、ログファイルに記録します。  
`str` この文字列は記録されます。

	log( "Hello World!" )
	log( tostring(managers.player:player_unit():key()) )

### dohttpreq( url, callback(data, id), [progress_callback(id, bytes, total_bytes)] )
指定したURLへの HTTP/S リクエストを実行します。 成功した場合、取得されたデータをコールバックに返します。  
`url` リクエストを実行するURL。  
`returns` HTTP/SリクエストのID。  

`callback(data, id)` データが取得された場合に実行される関数です。  
`callback: data` サーバーから返されたデータ。String型で返されます。  
`callback: id` HTTP/SリクエストのID。  

`progress_callback(id, bytes, total_bytes)` HTTP/Sリクエストが進捗状況を返すときにこの関数が実行されます。 これはオプションです。  
`progress_callback: id` 進捗状況を返しているHTTP/SリクエストのID。  
`progress_callback: bytes` 受信した現在のバイト数。  
`progress_callback: total_bytes` HTTP/Sリクエストを完了するために必要なダウンロードの合計バイト数。  

	dohttpreq( "http://google.com/", function(data, id)
		log( "Retrieved server data:\n" .. data )
	end )

	dohttpreq( "http://paydaymods.com/mybigfile.zip",
		function(data, id)
			log( "Retrieved server data:\n" .. data )
		end,
		function(id, bytes, total_bytes)
			log( id .. " downloaded " .. tostring(bytes) .. " / " .. tostring(total_bytes) .. " bytes")
		end
	)

### unzip( zip_file, extract_dir )
指定された `zip_file` を `extract_dir` に解凍します。 解凍速度は遅く、マルチスレッド処理では **ありません** 。また、メニューを開いている間のみに行われるべきです。  
`zip_file` 解凍したいZIPファイル。  
`extract_dir` ZIPファイルの解凍先。  

	local zip = "mods/base/downloads/goonmod.zip"
	local mods_folder = "mods/"
	unzip( zip, mods_folder )
