# sgt-fields

[![NPM](https://nodei.co/npm/sgt-fields.png)](https://nodei.co/npm/sgt-fields/)

[![NPM version](https://img.shields.io/npm/v/sgt-fields.svg)](https://www.npmjs.com/package/sgt-fields) [![Build Status](https://travis-ci.org/rodrigocmoreira/sgt-fields.svg?branch=master)](https://travis-ci.org/rodrigocmoreira/sgt-fields) [![Quality Gate](https://sonarcloud.io/api/project_badges/measure?project=sgt-fields&metric=alert_status)](https://sonarcloud.io/dashboard/index/sgt-fields) [![NPM monthly downloads](https://img.shields.io/npm/dm/sgt-fields.svg)](https://www.npmjs.com/package/sgt-fields) [![NPM total downloads](https://img.shields.io/npm/dt/sgt-fields.svg)](https://www.npmjs.com/package/sgt-fields) [![Coverage Status](https://coveralls.io/repos/github/rodrigocmoreira/sgt-fields/badge.svg?branch=master)](https://coveralls.io/github/rodrigocmoreira/sgt-fields?branch=master) [![Known Vulnerabilities](https://snyk.io/test/npm/sgt-fields/badge.svg)](https://snyk.io/test/npm/sgt-fields)

Find the property in your object with Sargent Fields

## Install

Install with [npm](https://www.npmjs.com/):

```sh
npm install sgt-fields --save
```

## Usage

```js
var sgtFields = require('sgt-fields');
```

Get property on object:

```js
var object = {
  a: {
    b: {
      c: 'test'
    }
  }
};
var result = sgtFields.get(object, 'a.b.c');
//=> result = 'test'
```

Get property on object (supported array):

```js
var object = {
  user: {
    fullName: [{
      name: 'first name'
    }, {
      name: 'second name'
    }]
  }
};
var resultFirstName = sgtFields.get(object, 'user.fullName.0.name');
//=> resultFirstName = 'first name'

var resultSecondName = sgtFields.get(object, 'user.fullName.1.name');
//=> resultSecondName = 'second name'
```

Set or add property on object:

```js
var object = {
  a: {
  }
};
var result = sgtFields.set(object, 'a.b.c', 'test');
//=> result = { a: { b: { c: 'test' } } }
//=> object = { a: { b: { c: 'test' } } }
```

Loop through each property on object:

```js
var object = {
  name: 'Fields',
  rank: 'Sgt',
  personalInfo: {
    phone: '987654321',
    email: 'sgt-fields@sgt-fields.com'
  }
};

sgtFields.each(object, (field, value) => {
  console.log(field, value);
});
//=> name Fields
//=> rank Sgt
//=> personalInfo { phone: '987654321', email: 'sgt-fields@sgt-fields.com' }
```
