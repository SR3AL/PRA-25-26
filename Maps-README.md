# Summary ahead of the Second PRA Practice Exam 25/26

Here you'll find a summary of all about Maps/Dictionaries, disadvantages, advantages in front of other data structures. <br> This is a theoretical summary where you'll find the main concepts with detailed explanations and examples to help you understand better this data structure.

## Maps/Dictionaries
A _Map_ ( also known as a _Dictionary_ ) is an abstract data type that stores elements in key-value pairs.

The <span style="font-weight:bold; color: #279FBA">key</span> is always simple data type (string, integer, etc) while the <span style="font-weight:bold; color: #279FBA">value</span> can be any data type (simple or complex).

For using Maps/Dictionaries in C++, you can use the library `#include <map>`. <br>

Here you have an example of how to create a Map/Dictionary in C++:

```cpp
#include <map>
#include <string>
#include <iostream>

using namespace std;

int main(){
    map<string, string> myDictionary;
    myDictionary.insert(pair<string,string>("apple", "der Apfel"));
    myDictionary.insert(pair<string,string>("banana", "die Banane"));
}
```

If you would like to print the values of the Map/Dictionary, you can do it like this:

```cpp
for(auto pair : myDictionary) {
    cout << pair.first << " - " << pair.second << endl;
}
```

> [!NOTE]
> An important characteristic of Map collection is that it orders elements by key in ascending order which means that if your key is a string, then the elements will be ordered alphabetically. <br> If your key is an integer, then the elements will be ordered from the smallest to the biggest number.

> [!IMPORTANT]
> If you would like to have an unordered Map/Dictionary in C++, you can use the library `#include <unordered_map>`. Also, you might change the declaration of the Map/Dictionary from `map<key_type, value_type>` to `unordered_map<key_type, value_type>`.

### How to access to a specific element

In order to access to a specific element, you use its key and you use square brackets `[]` like this:

```cpp
myDictionary["apple"]; // it will return "der Apfel"
```

> [!CAUTION]
> Keys have to be unique. If you try to insert a new element with a key that already exists in the Map/Dictionary, the value of that key will be updated with the new value.

If you would like to change the value of a specific key, you can do it like this:

```cpp
myDictionary["apple"] = "Die Erdbeere"; // it will update the value of the key "apple"
cout << myDictionary["apple"]; // it will return "Die Erdbeere"
```

If you want to clear all the elements of the Map/Dictionary, you can use the method `clear()` like this:

```cpp
myDictionary.clear(); // it will remove all the elements of the Map/Dictionary
```

> [!NOTE]
> You can also use the method `erase(key)` to remove a specific element from the Map/Dictionary by using its key. For example: `myDictionary.erase("apple");` will remove the element with the key "apple".

### Example of Map/Dictionary usage

For explaining better the usage of complex data type in Maps/Dictionaries, here you have an example.

#### <span style="text-decoration: underline">Pokemon Pokedex</span>
On this example, we'll create a <span style = "color: #FFCF38; font-weight: bold;">Pokedex</span> using a Map/Dictionary where the key _(simple data type)_ will be the name of the Pokemon and the value _(complex data type)_ will be its type.

```cpp
#include <map>
#include <string>
#include <iostream>
#include <list>

using namespace std;

int main(){
    map<string, list<string>> pokedex;

    list<string> pikachuAttacks{"Electric Shock", "Quick Attack", "Thunderbolt"};
    list<string> charmanderAttacks{"Ember", "Scratch", "Flamethrower"};
    list<string> bulbasaurAttacks{"Vine Whip", "Tackle", "Razor Leaf"};

    pokedex.insert(pair<string, list<string >> ("Pikachu", pikachuAttacks));
    pokedex.insert(pair<string, list<string >> ("Charmander", charmanderAttacks));
    pokedex.insert(pair<string, list<string >> ("Bulbasaur", bulbasaurAttacks));

    for(auto pokemon : pokedex){ // it prints all pokemons in pokedex with their attacks
        cout << pokemon.first << " attacks: ";
        for(auto attack : pokemon.second){
            cout << attack << ", ";
        }
        cout << endl;
    }
    return 0;
}