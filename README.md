# Fizz-Buzz-MongoDB
Implemented the Fizz Buzz game in MongoDB using the Mongo shell

[Fizz Buzz Rules!](https://en.wikipedia.org/wiki/Fizz_buzz)

**Step 1: Create the database, collection, and seed with data**

```javascript

//create database
use fizzbuzzdb

//create collection
db.createCollection("fizzbuzz");

//add seed data
db.fizzbuzz.insert([
{
  "value_check": 1
}, {
  "value_check": 2
}, {
  "value_check": 3
}, {
  "value_check": 4
}, {
  "value_check": 5
}, {
  "value_check": 6
}, {
  "value_check": 7
}, {
  "value_check": 8
}, {
  "value_check": 9
}, {
  "value_check": 10
}, {
  "value_check": 11
}, {
  "value_check": 12
}, {
  "value_check": 13
}, {
  "value_check": 14
}, {
  "value_check": 15
}, {
  "value_check": 16
}, {
  "value_check": 17
}, {
  "value_check": 18
}, {
  "value_check": 19
}, {
  "value_check": 20
}, {
  "value_check": 21
}, {
  "value_check": 22
}, {
  "value_check": 23
}, {
  "value_check": 24
}, {
  "value_check": 25
}, {
  "value_check": 26
}, {
  "value_check": 27
}, {
  "value_check": 28
}, {
  "value_check": 29
}, {
  "value_check": 30
}, {
  "value_check": 31
}, {
  "value_check": 32
}, {
  "value_check": 33
}, {
  "value_check": 34
}, {
  "value_check": 35
}, {
  "value_check": 36
}, {
  "value_check": 37
}, {
  "value_check": 38
}, {
  "value_check": 39
}, {
  "value_check": 40
}, {
  "value_check": 41
}, {
  "value_check": 42
}, {
  "value_check": 43
}, {
  "value_check": 44
}, {
  "value_check": 45
}, {
  "value_check": 46
}, {
  "value_check": 47
}, {
  "value_check": 48
}, {
  "value_check": 49
}, {
  "value_check": 50
}, {
  "value_check": 51
}, {
  "value_check": 52
}, {
  "value_check": 53
}, {
  "value_check": 54
}, {
  "value_check": 55
}, {
  "value_check": 56
}, {
  "value_check": 57
}, {
  "value_check": 58
}, {
  "value_check": 59
}, {
  "value_check": 60
}, {
  "value_check": 61
}, {
  "value_check": 62
}, {
  "value_check": 63
}, {
  "value_check": 64
}, {
  "value_check": 65
}, {
  "value_check": 66
}, {
  "value_check": 67
}, {
  "value_check": 68
}, {
  "value_check": 69
}, {
  "value_check": 70
}, {
  "value_check": 71
}, {
  "value_check": 72
}, {
  "value_check": 73
}, {
  "value_check": 74
}, {
  "value_check": 75
}, {
  "value_check": 76
}, {
  "value_check": 77
}, {
  "value_check": 78
}, {
  "value_check": 79
}, {
  "value_check": 80
}, {
  "value_check": 81
}, {
  "value_check": 82
}, {
  "value_check": 83
}, {
  "value_check": 84
}, {
  "value_check": 85
}, {
  "value_check": 86
}, {
  "value_check": 87
}, {
  "value_check": 88
}, {
  "value_check": 89
}, {
  "value_check": 90
}, {
  "value_check": 91
}, {
  "value_check": 92
}, {
  "value_check": 93
}, {
  "value_check": 94
}, {
  "value_check": 95
}, {
  "value_check": 96
}, {
  "value_check": 97
}, {
  "value_check": 98
}, {
  "value_check": 99
}, {
  "value_check": 100
}
]);
```

**Step 2: Query values and determine Fizz Buzz results**

```javascript
// Query the fizzbuzz collection and display the appropriate results based on rules below.
// Rules: Any number divisible by three is replaced by the word fizz
//        and any divisible by five by the word buzz. Numbers divisible 
//        by both become fizz buzz.

db.fizzbuzz.aggregate([{
  $project: 
  {
	_id: 0,
	"value_check": 1,
    "results": 
    {
        $switch: 
      {
          branches: [
        {
        case: { 
          $and: [ 
            { $eq: [ {$mod: [ "$value_check", 3 ]}, 0] }, 
            { $eq: [ {$mod: [ "$value_check", 5 ]}, 0] }
          ]
        }, 
        then: "fizzbuzz"
        },		
            { 
              case: { $eq: [ {$mod: [ "$value_check", 3 ]}, 0 ] }, 
              then: "fizz"
            },
        {
        case: { $eq: [ {$mod: [ "$value_check", 5 ]}, 0 ] }, 
              then: "buzz"
        }
      ],
      default: "$value_check"
      }
    }
  }
}]);
```


