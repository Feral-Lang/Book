# Lang

The **lang** module offers a way to create user-defined structures and enumerations.

A structure can pack together variables and functions, which allow object-oriented programming.

An enumeration is a set of names bounds to constant numerical values.
```
let lang = import('std/lang');
```

## Functions
- [struct](#struct)
- [enum](#enum)

### Struct
```
lang.struct(field = value, ...) -> type
```
Creates a new structure type type holding a set of `field`s. The given `value`s are used to infer the type of each field and as default values during construction. The return type can be used to instantiate objects of this type.

Adding member functions to a type is done with the `let func in type = fn(args) {}` construct, with `func` being the function's name. Inside the function, variables and functions belonging to the type can be accessed using the `self` keyword.

Example:
```
let io = import('std/io');
let player_t = lang.struct(name = "John", class = "Mage", health = 100, attack = 10);

# str is used by print functions to print the content of an object
let str in player_t = fn() {
    let desc = '';
    desc += "name: " + self.name.str();
    desc += ", class: " + self.class.str();
    desc += ", health: " + self.health.str();
    desc += ", attack: " + self.attack.str();
    return desc;
};

let take_damage in player_t = fn(damage) {
    io.println('Taking ', damage, ' damage');
    self.health -= damage;
    return self;
};

let player = player_t("Bob", attack = 20);  # Positional and named arguments allowed
io.println(player);                         # Calls player.str()
player.take_damage(30).take_damage(10);     # Possible thanks to 'return self'
io.println(player);
```

Gives the output:
```
name: Bob, class: Mage, health: 100, attack: 20
Taking 30 damage
Taking 10 damage
name: Bob, class: Mage, health: 60, attack: 20
```

### Enum
```
lang.enum(.name1, .name2 = value, ...) -> type
```
Creates a new enumeration with the given `name`s and optionally given `value`s. Names must be prefixed with a dot.

Example:
```
let class = lang.enum(.Mage, .Warrior, .Mecromancer, .Unknown = -1);
let player_t = lang.struct(name = "John", class = class.Unknown, health = 100, attack = 10);

let str in player_t = fn() {
    let desc = '';
    desc += "name: " + self.name.str();
    desc += ", class: " + self.class.str();
    desc += ", health: " + self.health.str();
    desc += ", attack: " + self.attack.str();
    return desc;
};

io.println(player_t("Bob", class.Mage));
io.println(player_t("Josh"));
```

Gives the output:
```
name: Bob, class: 0, health: 100, attack: 10
name: Josh, class: -1, health: 100, attack: 10
```