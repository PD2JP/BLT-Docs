
### file.GetDirectories(_path_)
PATDAY2実行ファイルから見た指定された相対パスの全ての子ディレクトリを取得します。    
* `path`: 子ディレクトリを取得するパス。  
```lua
file.GetDirectories("mods/")
```
### file.GetFiles(_dir_)
`dir` 内の全てのファイルを取得します。  
* `dir`: ファイルを取得するディレクトリ。  
```lua
file.GetFiles("mods/base/lua/")
```
### file.RemoveDirectory(_path_)  
`path` が空だった場合、そのディレクトリを削除します。  
* `path`: 削除するディレクトリのパス。  
* `戻り値`: 削除に成功した場合は `true` が 失敗した場合は `false` が返されます。  
```lua
local removed = file.RemoveDirectory("mods/my_mod/")
```
### file.DirectoryExists(_path_)
`path` が存在しているかどうかを確認します。  
* `path`: 存在しているかどうかを確認するパス。  
* `戻り値`: ディレクトリが存在する場合は `true` が 存在しない場合は `false` が返されます。  
```lua
local path = "mods/my_mod/"
if file.DirectoryExists(path) then
	file.RemoveDirectory(path)
end
```
### io.file_is_readable(*file_path*)
`file_path` のファイルが Lua state によって開くことができるかどうかを確認します。   
* `file_path`: 開くことができるかどうかを確認するパス。  
* `戻り値`: ファイルを開くことができる場合は `true` が その他の場合は `false` が返されます。  
```lua
local path = "mods/saves/save_data.lua"
if io.file_is_readable(path) then
	-- ファイルを読み込む処理
end
```
### io.remove_directory_and_files(*path*)
指定された `path` に存在する全てのファイル及びフォルダーを再帰的に削除します。  
* `path`: 全てのファイル及びフォルダーを削除するパス。  
* `戻り値`: 全てのファイル及びフォルダーの削除に成功した場合は `true` が 実行途中に削除できないファイルやフォルダーが存在した場合は `false` が返されます。  
```lua
local function uninstall_my_mod()
	io.remove_directory_and_files("mods/my_mod/")
end
```