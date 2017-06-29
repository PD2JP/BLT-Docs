
# Mod定義ファイル

Your mod definition file is what the Payday 2 BLT uses to load your mod. It is a json-formatted text file in your mod directory.  
To setup your definition, simply create a text file `mod.txt` in your mod directory, and setup your required basic details, hooks,
persist-scripts, and keybinds.  

---

### 基本的なMod定義

あなたのModの基本的な定義。 あなたのModの基本的な情報が含まれます。  

* `name`: Mod名 (わかりやすい物が良いです)  
* `description`: Modの説明 Modが何をするかなど。  
* `author`: あなたや貢献者などModを作るのに関わった人。  
* `contact`: Mod利用者があなたに連絡するための連絡先。  
* `version`: わかりやすいModのバージョン。ゲーム内のModマネージャーに表示されます。  
* `priority`: 0 から 1000の間の数値。他のmodとの読み込み順を決定するために使用されます。依存しているmodがある際に使用するべきです。  
```json
{
	"name": "テストMOD",
	"description": "何もしないテストMOD",
	"author": "James Wilkinson",
	"contact": "jw@jameswilko.com",
	"version": "1.0",
	"priority": 10
}
```
### Hooks

_Previously Post-Require Scripts in PD2Hook.yml_  
The Payday 2 files to hook and run a specified lua script after. The hooks key is an array of objects.

`hooks` The array of objects containing a `hook_id` and a `script_path`.  
`hook_id` The Payday 2 script file to run the script in `script_path` after.  
`script_path` The path to your Lua script to run. This is relative to your mod folder.  

	"hooks" : [
		{ 	
			"hook_id" : "lib/setups/gamesetup",
			"script_path" : "PostGameSetup.lua"
		},
		{ 	
			"hook_id" : "lib/managers/menu/blackmarketgui",
			"script_path" : "BlackMarketGUIStuff.lua"
		}
	]

### Pre-Hooks

_Previously Pre-Require Scripts in PD2Hook.yml_
Identical to `Hooks`, except that these will run **before** the Payday 2 script defined in `hook_id`.

`pre_hooks` The array of objects containing a `hook_id` and a `script_path`.  
`hook_id` The Payday 2 script file to run the script in `script_path` before.  
`script_path` The path to your Lua script to run. This is relative to your mod folder.  

	"pre_hooks" : [
		{ 	
			"hook_id" : "lib/setups/menusetup",
			"script_path" : "PreSetupMenu.lua"
		}
	]

### 永続的なスクリプト

_Previous Persist-Scripts in PD2Hook.yml_  
A script in `script_path` which is run every frame until the global variable specified in `global` is set to anything other than false or nil.  

`persist_scripts` The array of objects containing a `global` and a `script_path`.  
`global`  The global value to associate with `script_path`.  
`script_path` The script to continuously run until the global variable `global` is set to a value other than false or nil.  

	"persist_scripts" : [
		{
			"global" : "MyGlobalValue",
			"script_path" : "TestPersistScript.lua"
		},
		{
			"global" : "NotPocoHud",
			"script_path" : "not_poco/hud.lua"
		}
	]

### Jsonキーバインド

_Previously Keybinds in PD2Hook.yml_  
A script to run when a key is pressed. These keybinds can be customized in-game, instead of being set to a specific hard-coded key.  

`keybinds` An array containing generic keybind information. Each keybind will be saved and loaded automatically for you.   
`keybind_id` A unique ID for your keybind. Your keybind will be saved and loaded via this ID, so make sure that it relates to your mod so that no other mods can override it.  
`name` The name of the keybind to display in the keybinds menu.  
`description` A short of description of your keybind.  
`script_path` The path to the script that should be ran when the keybind is pressed.  
`run_in_menu` A boolean of whether this keybind should run when pressed during the menu state.  
`run_in_game` A boolean of whether this keybind should run when pressed during the game state.  
`localized` A boolean of if the menu should attempt to use the name and description as localization keys.
Use `false` if you wish to just type a name and description in.

	"keybinds" : [
		{
			"keybind_id" : "keybind_example_test",
			"name" : "Test Keybind",
			"description" : "An example keybind for demonstration",
			"script_path" : "test.lua",
			"run_in_menu" : true,
			"run_in_game" : true,
			"localized" : false
		}
	]

### 完全な記述例
```json
{
	"name": "テストMOD",
	"description": "何もしないテストMOD",
	"author": "James Wilkinson",
	"contact": "jw@jameswilko.com",
	"version": "1.0",
	"hooks": [
		{
			"hook_id": "lib/setups/gamesetup",
			"script_path": "PostGameSetup.lua"
		},
		{
			"hook_id": "lib/managers/menu/blackmarketgui",
			"script_path": "BlackMarketGUIStuff.lua"
		}
	],
	"persist_scripts" : [
		{
			"global": "MyGlobalValue",
			"script_path": "TestPersistScript.lua"
		}
	],
	"keybinds" : [
		{
			"keybind_id": "keybind_example_test",
			"name": "Test Keybind",
			"description": "An example keybind for demonstration",
			"script_path": "test.lua",
			"run_in_menu": true,
			"run_in_game": true,
			"localized": false
		}
	]
}
```