## 2.8.0 - April 1th, 2021. Not a joke :P

* `._update()` data now may be `null` if it has the `undefined` type, so the developer may remove a optional property while updating, as passing `undefined` keeps the value.

## 2.7.3~4 - March 29th, 2021

* Added Id<> wrapper to NullableModelLike<>. This improves the return type of ._onceVal, ._dataFromDb etc.

## 2.7.2 - December 28th, 2020

* Improved `_dataFromDb` return type.

## 2.7.1 - December 28th, 2020

* Fixed typo in `committed`, in `._transaction()` return.

## 2.7.0 - December 28th, 2020

* Changed `._transaction()` return to allow the check of `commited` status.

* Changed `._dataFromDb()` data type, to avoid passing snapshots instead of snapshot.val().


## 2.6.0~2 - December 28th, 2020

* Added `._transaction()`!

* Fixed _dataFromDb not including null in return type as union [#1](https://github.com/SrBrahma/Firebase-Database-Modeler/issues/1)


## 2.5.2 - October 9th, 2020

* Added `._dbTypeNoNull`


## 2.5.0~1 - October 8th, 2020

Added `._onConnected()` and `._onServerTimeOffset()` on any _root Node. They are a shortcut for

https://firebase.google.com/docs/database/web/offline-capabilities#section-connection-state and https://firebase.google.com/docs/database/web/offline-capabilities#clock-skew.

Their README sections will be added later, as I am in a rush to finish my App.

## 2.4.1~5 - October 8th, 2020

Fixed breaking change of 2.4.0. Now it should work properly.


## 2.4.0 - October 7th, 2020 4:28pm

Any null or undefined node are now optional, via `_<T | null>()` or `_<T | undefined>()`. Parents of `_$()` are now automatically optional. README about this will be added later.


## 2.3.0 - October 5th, 2020

- Added `._childrenNodeKeys`, an string[] of the Node children that are Node. Internal usage.

- Changed `._varNodeChild` (: Reference) to `._varNodeChildKey` (: string | undefined), for better ._clone'ing.

- Fixed `._clone` with self referencing data. This happened to me when passing a database to _root() or ._clone(),
as it self references.

- Due to changes above, improved `._clone` performance.

- Improved performance in `dataToDb` and `dataFromDb`.

- Refactored part of the code (`Node` and `_()`) to remove type forcing.


### 2.2.4

- Fixed `._pathTo` returning an empty string sometimes

### 2.2.3

- Fixed `._path` not starting with `/`. (cosmetic).

- Fixed `._push` on a VarNode parent not using the VarNode child in the `dataToDb` conversion.

### 2.2.2

- Fixed `._pathWithVars()`-like functions not working with string (not string[]) var.

### 2.2.1

- Improved invalid `vars` in `._ref()`-like functions. It now also shows the non parsed path.

## 2.2.0

- Added `blockDatabase` parameter to the `_root` and `._clone` functions.

- Also added `._blockDatabase` property which reflexes the parameter above.

- Fixed `._clone` not using the `database` parameter.

### 2.1.x

-  Fixed `._push()` not allowing no args

-  Fixed `._push()` return

## 2.1.0

-  Added `database` to the `_root()` and `._clone()` functions.

# Major 2.0.0 - September 25th, 2020

-  Changed variadic `...vars: string[]` to `vars?: string | string[]`.

-  Added `database` parameter to all database related model methods, allowing multiple Realtime Database instances.

-  Removed `finishModel()`. You now have to call `_root()` in your root Node instead of just `_()`.

-  Renamed `modelerSetDatabase` to `modelerSetDefaultDatabase`