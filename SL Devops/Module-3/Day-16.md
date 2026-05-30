## Task - 1
```
nano hello.sh
```
```
#!/bin/bash

echo "Hello Devops!"
```

## Task - 2
```
name="rtvk"
role="devops engg"
echo "Hello, I am $name and i am a $role"
```


Single Quotes (')
Variables are treated as plain text.

## Task -3
```                                                               
#!/bin/bash

read -p "Whats your name?" name
read -p "Fav tool" tool
echo "hello $name, your fav tool is $tool"
```

## Task -4
```
#!/bin/bash

echo "Enter a number:"
read NUM

if [ $NUM -gt 0 ]; then
    echo "The number is positive."
elif [ $NUM -lt 0 ]; then
    echo "The number is negative."
else
    echo "The number is zero."
fi
```

```
#!/bin/bash

echo "Enter filename:"
read FILE

if [ -f "$FILE" ]; then
    echo "File exists."
else
    echo "File does not exist."
fi
```

## Task-5
```
#!/bin/bash

read -p "Enter the service name: " service
read -p "Do you want to check the status(y/n): " status

if [ "$status" = "y" ]; then
        systemctl status "$service"
else 
        echo "skipped"
fi
```





