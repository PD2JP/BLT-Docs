
### file.GetDirectories( path )
PATDAY2実行ファイルから見た指定された相対パスの全ての子ディレクトリを取得します。    
`path` 子ディレクトリを取得するパス。  

	file.GetDirectories( "mods/" )

### file.GetFiles( dir )
`dir` 内の全てのファイルを取得します。  
`dir` ファイルを取得するディレクトリ。  

	file.GetFiles( "mods/base/lua/" )

### file.RemoveDirectory( path )  
`path` が空だった場合、そのディレクトリを削除します。  
`path` 削除するディレクトリのパス。  
`returns` 削除に成功した場合は `true` が 失敗した場合は `false` が返されます。  

	local removed = file.RemoveDirectory( "mods/my_mod/" )

### file.DirectoryExists( path )
`path` が存在しているかどうかを確認します。  
`path` 存在しているかどうかを確認するパス。  
`returns` ディレクトリが存在する場合は `true` が 存在しない場合は `false` が返されます。  

	local path = "mods/my_mod/"
	if file.DirectoryExists( path ) then
		file.RemoveDirectory( path )
	end

### io.file_is_readable( file_path )
`file_path` のファイルが Lua state によって開くことができるかどうかを確認します。   
`file_path` 開くことができるかどうかを確認するパス。  
`returns` ファイルを開くことができる場合は `true` が その他の場合は `false` が返されます。  

	local path = "mods/saves/save_data.lua"
	if io.file_is_readable( path ) then
		-- Read file
	end

### io.remove_directory_and_files( path )
指定された `path` に存在する全てのファイル及びフォルダーを再帰的に削除します。  
`path` 全てのファイル及びフォルダーを削除するパス。  
`returns` 全てのファイル及びフォルダーの削除に成功した場合は `true` が 実行途中に削除できないファイルやフォルダーが存在した場合は `false` が返されます。  

	local function uninstall_my_mod()
		io.remove_directory_and_files( "mods/my_mod/" )
	end
