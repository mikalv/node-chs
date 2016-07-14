# CHS (Cylinder-Head-Sector) Address
[![npm](https://img.shields.io/npm/v/chs.svg?style=flat-square)](https://npmjs.com/package/chs)
[![npm license](https://img.shields.io/npm/l/chs.svg?style=flat-square)](https://npmjs.com/package/chs)
[![npm downloads](https://img.shields.io/npm/dm/chs.svg?style=flat-square)](https://npmjs.com/package/chs)
[![build status](https://img.shields.io/travis/jhermsmeier/node-chs.svg?style=flat-square)](https://travis-ci.org/jhermsmeier/node-chs)

[CHS addressing] is an early method for giving addresses to each physical block of data on a hard disk drive,
identifying individual sectors on a disk by their position in a track, where the track is determined by the head and cylinder numbers.

[CHS addressing]: https://en.wikipedia.org/wiki/Cylinder-head-sector

# Install via [npm](https://npmjs.com)

```sh
$ npm install --save chs
```

# Usage

```js
// Load module
var CHS = require( 'chs' )
```
```js
// Create a CHS address
var addr = new CHS( 5, 20, 8 )
```
```js
// Properties:
var c = addr.cylinder
var h = addr.head
var s = addr.sector
```
```js
// Convert to an LBA (Logical Block Address)
var lba = addr.toLBA( headsPerTrack, sectorsPerTrack )
var lba = addr.toLBA( 12, 32 )
```
```js
// Set it to an LBA
addr.setLBA( lba, headsPerTrack, sectorsPerTrack )
addr.setLBA( 3150, 16, 63 )
```
```js
// Get it as a buffer
var buf = addr.buffer
var buf = addr.toBuffer()
```
```js
// Set from buffer
addr.buffer = new Buffer([ 0xFE, 0xFF, 0xFF ])
addr.parse( new Buffer([ 0xFE, 0xFF, 0xFF ]) )
```

# API Reference
<a name="CHS"></a>

## CHS
**Kind**: global class

* [CHS](#CHS)
    * [new CHS([cylinder], [head], [sector])](#new_CHS_new)
    * _instance_
        * [.cylinder](#CHS+cylinder) : <code>Number</code>
        * [.head](#CHS+head) : <code>Number</code>
        * [.sector](#CHS+sector) : <code>Number</code>
        * [.buffer](#CHS+buffer) : <code>Buffer</code>
        * [.setLBA(lba, hpt, spt)](#CHS+setLBA) ⇒ <code>[CHS](#CHS)</code>
        * [.getLBA(hpt, spt)](#CHS+getLBA) ⇒ <code>Number</code>
        * [.toLBA(hpt, spt)](#CHS+toLBA) ⇒ <code>Number</code>
        * [.clone()](#CHS+clone) ⇒ <code>[CHS](#CHS)</code>
        * [.copy(target)](#CHS+copy) ⇒ <code>[CHS](#CHS)</code>
        * [.parse(buffer)](#CHS+parse) ⇒ <code>[CHS](#CHS)</code>
        * [.toBuffer()](#CHS+toBuffer) ⇒ <code>Buffer</code>
    * _static_
        * [.fromBuffer(buffer)](#CHS.fromBuffer) ⇒ <code>[CHS](#CHS)</code>
        * [.fromLBA(lba, hpt, spt)](#CHS.fromLBA) ⇒ <code>[CHS](#CHS)</code>


-

<a name="new_CHS_new"></a>

### new CHS([cylinder], [head], [sector])
Cylinder-Head-Sector Address

**Params**

- [cylinder] <code>Number</code> | <code>Buffer</code> <code> = 1023</code>
- [head] <code>Number</code> <code> = 254</code>
- [sector] <code>Number</code> <code> = 63</code>


-

<a name="CHS+cylinder"></a>

### chS.cylinder : <code>Number</code>
Cylinder

**Kind**: instance property of <code>[CHS](#CHS)</code>

-

<a name="CHS+head"></a>

### chS.head : <code>Number</code>
Head

**Kind**: instance property of <code>[CHS](#CHS)</code>

-

<a name="CHS+sector"></a>

### chS.sector : <code>Number</code>
Sector

**Kind**: instance property of <code>[CHS](#CHS)</code>

-

<a name="CHS+buffer"></a>

### chS.buffer : <code>Buffer</code>
Get/set values from/to a Buffer

**Kind**: instance property of <code>[CHS](#CHS)</code>

-

<a name="CHS+setLBA"></a>

### chS.setLBA(lba, hpt, spt) ⇒ <code>[CHS](#CHS)</code>
Set CHS to a Logical Block Address (LBA)

**Kind**: instance method of <code>[CHS](#CHS)</code>
**Params**

- lba <code>Number</code> - Logical Block Address
- hpt <code>Number</code> - Heads per Track
- spt <code>Number</code> - Sectors per Track


-

<a name="CHS+getLBA"></a>

### chS.getLBA(hpt, spt) ⇒ <code>Number</code>
Get the Logical Block Address (LBA)
corresponding to the given disk geometry

**Kind**: instance method of <code>[CHS](#CHS)</code>
**Returns**: <code>Number</code> - lba
**Params**

- hpt <code>Number</code> - Heads per Track
- spt <code>Number</code> - Sectors per Track


-

<a name="CHS+toLBA"></a>

### chS.toLBA(hpt, spt) ⇒ <code>Number</code>
**Kind**: instance method of <code>[CHS](#CHS)</code>
**Returns**: <code>Number</code> - lba
**See**: #getLBA()
**Params**

- hpt <code>Number</code> - Heads per Track
- spt <code>Number</code> - Sectors per Track


-

<a name="CHS+clone"></a>

### chS.clone() ⇒ <code>[CHS](#CHS)</code>
Clone the CHS Address

**Kind**: instance method of <code>[CHS](#CHS)</code>

-

<a name="CHS+copy"></a>

### chS.copy(target) ⇒ <code>[CHS](#CHS)</code>
Copy this address to a target address

**Kind**: instance method of <code>[CHS](#CHS)</code>
**Params**

- target <code>[CHS](#CHS)</code>


-

<a name="CHS+parse"></a>

### chS.parse(buffer) ⇒ <code>[CHS](#CHS)</code>
Parse a given Buffer

**Kind**: instance method of <code>[CHS](#CHS)</code>
**Params**

- buffer <code>Buffer</code>


-

<a name="CHS+toBuffer"></a>

### chS.toBuffer() ⇒ <code>Buffer</code>
Create a Buffer representation of the CHS Address

**Kind**: instance method of <code>[CHS](#CHS)</code>

-

<a name="CHS.fromBuffer"></a>

### CHS.fromBuffer(buffer) ⇒ <code>[CHS](#CHS)</code>
Create a CHS Address from a given buffer

**Kind**: static method of <code>[CHS](#CHS)</code>
**Params**

- buffer <code>Buffer</code>


-

<a name="CHS.fromLBA"></a>

### CHS.fromLBA(lba, hpt, spt) ⇒ <code>[CHS](#CHS)</code>
Create a CHS Address from a Logical Block Address (LBA)

**Kind**: static method of <code>[CHS](#CHS)</code>
**Params**

- lba <code>Number</code> - Logical Block Address
- hpt <code>Number</code> - Heads per Track
- spt <code>Number</code> - Sectors per Track


-

