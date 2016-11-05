
# 遅延呼び出し

遅延呼び出しは設定された時間分だけ関数の呼び出しを遅延させることができます。  
この機能は秒数のみで指定することができます。
もし、あなたが特定のイベントが発生したときや他の関数が走ったときなどに実行をさせたいならば [`Hooks`](hooks.md) を代わりに使うと良いでしょう。 

---

### DelayedCalls:Add( id, time, func )
指定された秒数が経過後、自動的に実行される 遅延呼び出し を追加します。  
`id` この遅延呼び出しのユニークな名前です。  
`time` 遅延させる秒数です。 `func` が指定秒数経過後に実行されます。  
`func` `time` で指定した秒数が経過後に実行される関数です。  

	DelayedCalls:Add( "DelayedCallsExample", 5, function()
		log("This will be called after 5 seconds.")
	end )

### DelayedCalls:Remove( id )
指定された `id` を持つ 遅延呼び出し を削除します。  
`id` が存在しない場合やすでに実行されていた場合、この関数は何もしません。  
`id` 削除する 遅延呼び出し のユニークな名前です。  

	DelayedCalls:Remove( "DelayedCallsExample" )

