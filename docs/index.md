---
  hide:
    - toc
    - navigation
---

<div id="bytenet-header">
	<h1>simple buffer-based networking</h1>
	<p>
		In ByteNet, you don't need to worry about type validation, optimization, packet structure, etc. ByteNet does all the hard parts for you! Strictly typed with an incredibly basic API that explains itself, ByteNet makes networking simple, easy, and quick.
	</p>
	<span id="linkspan">
		<a href="./api/functions/definePacket" id="link">Getting started</a>
		<a href="https://github.com/ffrostflame/ByteNet/releases/latest" id="link">Download</a>
	</span>
	<hr />
	<p>
		<p id="small" align="right">
		<i>practical example of a packet's definition</i>
	</p>

	```lua title="packets.luau"
	local ByteNet = require(path.to.ByteNet)

	local packets = {
		myPacket = ByteNet.definePacket({
			structure = {
				-- A map where the key is a Vector3, and the value is a string
				map = ByteNet.dataTypes.map(ByteNet.dataTypes.vec3(), ByteNet.dataTypes.string())
			}
		})
	}
	```
</p>

<p id="small" align="left">
	<i>example of sending a packet to all clients</i>
</p>


```lua title="server.luau"
local packets = require(path.to.packets)

packets.myPacket:sendToAll({
	map = {
		[Vector3.new(1, 1, 1)] = "10x less bandwidth than a remote!",
		[Vector3.new(1, 2, 1)] = "oh wait, its way more than 10x less.",

		[Vector3.new(2, 1, 1)] = "depending on how you use your data,",
		[Vector3.new(1, 1, 2)] = "it could be 100x less!",
	}
})
```

</div>


---

# Not enough? here's more

## - No more RemoteEvents
ByteNet handles all instances for you; you don't need to worry about reliability type, parenting, etc

## - As low-level as you can get
ByteNet lets you directly read/write data types such as uint32, buffers, in a way where the keys are abstracted away. Reap the benefits of a structured, strictly typed library, while retaining the benefits of hardcore optimization.