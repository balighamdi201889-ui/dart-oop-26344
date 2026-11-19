 # Dart OOP Assignment: Kigali Bus Card

**Name:** balig hamdi badri ahmed
**Student ID:** 26344

## My numbers
D = 44
L = 4
Starting balance = 1440 RWF
Bus fare = 244 RWF
Student discount = 14%

## Output of main.dart
```text
Error: name too short
Owner: balig hamdi badri ahmed | Balance: 1440 RWF
Owner: balig hamdi badri ahmed | Balance: 1440 RWF
Error: top-up must be 500 to 50000 RWF
Topped up 2000 RWF
Paid 244 RWF
Paid 244 RWF
Owner: balig hamdi badri ahmed | Balance: 2952 RWF
Student discount: 34 RWF
Paid 210 RWF
Owner: balig hamdi badri ahmed | Balance: 1230 RWF
Student card: 14% off
```

## Part 1: Why no setter for balance?
Not having a setter for `_balance` protects the money from being changed directly to any arbitrary or negative value (for example, `card.balance = 999999`). Instead, all balance changes must go through controlled methods like `topUp()` and `pay()`, which enforce the business rules.

## Part 2: What does ~/ do?
The `~/` operator performs integer division, meaning it divides two numbers and drops the decimal part to return a whole number (`int`).
- `print(237 * 17 / 100);` prints `40.29` (a `double`).
- `print(237 * 17 ~/ 100);` prints `40` (an `int`, truncating the `.29`).

## Part 4: Bug table
| Bug | The line | Why it is wrong (your words) | Your fix |
| --- | --- | --- | --- |
| 1 | `String _brand; int _battery;` | Non-nullable fields must have an initial value in Dart. | Initialized them to `''` and `0`. |
| 2 | `SmartPhone(String brand, int battery, String system)` | The child constructor does not call the parent `Phone` constructor. | Added `: super(brand, battery)`. |
| 3 | `@override` above `void restart()` | The parent class `Phone` does not have a `restart()` method to override. | Removed `@override`. |
| 4 | `p.battery = 100;` | There is no setter for `battery` in the `Phone` class. | Added `set battery(int value)` that accepts 0 to 100. |
| 5 | `print(p.battery());` | `battery` is a getter, not a method, so it cannot be called with parentheses. | Changed it to `print(p.battery);`. |
| Not a bug | `Phone p = new Phone('Tecno', 50);` | The `new` keyword is optional in Dart, so writing it is still valid syntax. | (none) |

## Part 5
My prediction:
```text
1
5
```
Explanation: For `a`, `add()` increases `_items` to 1, and `a.items = -5` is ignored because the setter only accepts values `>= 0`, so it prints `1`. For `b` (`BigBag`), each `add()` calls `super.add()` twice, so two calls make `_items` equal to 4, then `b.items = b.items + 1` sets it to 5, so it prints `5`.

Real output:
```text
1
5
```

Was I right?
Yes, my prediction matched the real output completely.