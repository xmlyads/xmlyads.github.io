# Example

```thrift
service BoatRaceTimes {
    i16 BeginRace(1: i32 CourseID, 2: map<i32,i32> BoatsAndTeams),
    void ReportFinish(1: i16 RaceNumber, 2: i32 Boat, 3: bool DNF=false),
}
```

```java
enum Test {
    A,
    B,
    C,
    D
}

@Data
public static void main(String[] args) {

}
```

```php
$user = $svc->getUserById($id);
echo json_encode($user);
```

``` py title="bubble_sort.py"
def bubble_sort(items):
    for i in range(len(items)):
        for j in range(len(items) - 1 - i):
            if items[j] > items[j + 1]:
                items[j], items[j + 1] = items[j + 1], items[j]
```

``` yaml
theme:
  features:
    - content.code.annotate # (1)
```

1.  :man_raising_hand: I'm a code annotation! I can contain `code`, __formatted
    text__, images, ... basically anything that can be written in Markdown.
