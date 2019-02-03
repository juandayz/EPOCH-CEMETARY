# EPOCH-CEMETARY

PLEASE DONATE: https://github.com/juandayz/EPOCH-CEMETARY/blob/master/DONATION.md



Relocate all players corpses into cemetarys. with a grave, a cross and a box with all his items and coins. Cemetarys are randomly but you need define the random coords. Actually are seted in Chernarus Churchs. If u wanna change the locations edit those lines:

```ruby
_cemeteries = [
	[[5205.2866, 8582.541,0],"kabanino"],
	[[8332.0488, 5945.0884, 0],"kumyrna"],
	[[10020.204, 5512.1753,0],"staroye"],
	[[11184.681, 12290.43,0],"krasnostav"],
	[[8531.7148, 11980.951,0],"Gvozdno"],
	[[6201.606, 10397.821,0],"Grishino"],
	[[4569.5361, 6375.5166,0],"pogorevka"],
	[[7417.0859, 5195.2876,0],"mogilevka"]
];
```

INSTALL:

1-Open your custom compiles.sqf and made the call for player_death.sqf into !isDedicated section.

```ruby
player_death = compile preprocessFileLineNumbers "dayz_code\compile\player_death.sqf";
```

2.Drop player_death.sqf into MPMissions\your instance map\dayz_code\compile\

3.Open your custom fn_selfactions.sqf

Find:

```
if (_isMan && {!_isAlive} && {!(_cursorTarget isKindOf "Animal")} && {player distance _cursorTarget < 5}) then {
		if (s_player_checkWallet < 0) then {
			s_player_checkWallet = player addAction ["Check Wallet","scripts\zsc\checkWallet.sqf",_cursorTarget,0,false,true];
		};
	} else {
		player removeAction s_player_checkWallet;
		s_player_checkWallet = -1;
	};
```
  
  Replace by:
  
  ```ruby
  if ((_cursorTarget isKindOf "USOrdnanceBox_EP1") && {player distance _cursorTarget < 5}) then {
		if (s_player_checkWallet < 0) then {
			s_player_checkWallet = player addAction ["Money in tomb","scripts\zsc\checkWallet.sqf",_cursorTarget,0,false,true];
		};
	} else {
		player removeAction s_player_checkWallet;
		s_player_checkWallet = -1;
	};
  ```
Done.
