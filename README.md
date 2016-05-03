# Messagemus-Prime

A command-line utility for writing a message to the top of your terminal.

###Install with Homebrew

```
brew tap peledies/tap
brew install messagemus-prime
```

###Updating
```
brew update
brew upgrade messagemus-prime
```

##Example with arguments
```
messagemus-prime 'Title' 'John' 'Message Body'
```

##Example with a pipe |
```
echo -e "Title\n John\n Message Body" | messagemus-prime
```
