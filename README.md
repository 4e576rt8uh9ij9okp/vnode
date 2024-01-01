# About
Adds basic functionality to Vanilla code.
Has probably bugs and issues... I'm adding and changing things as I make my website; as only I depend on it for now :)

# $(tag :string, attributes :object, children :array)

### Simple Example:

    $("div", {className:"myClass"}, ["Hello World"])

    <div class="myClass">Hello World</div>

### Adding children:

    $("div", {className:"myClass"}, [
        $("div", {className:"myClass"}, ["Hello"]),
        $("div", {className:"myClass"}, ["World"])
    ])

    <div class="myClass">
        <div class="myClass">Hello</div>
        <div class="myClass">World</div>
    </div>

### Creating and adding children with listeners:

    const sendBtn = $("button", {className: "send-button"}, ["SEND"])
    sendBtn.addEventListener("click", e => {
        e.preventDefault()
        console.log("send")
    })

    $("div", {className:"myClass"}, [
        "Hello World",
        sendBtn
    ])
    
# class VNode(string | element)

### Simple example:

    let container = new VNode("#myContainer")

---

    let containerElement = $("div", {id: "myContainer"})
    let container = new VNode(containerElement)
    
### .clear()

Removes all children.

### .append(elements :array)

Appends an array of elements.

# class VList(string | element, config :object)

### config {template :function}
    {
        template: (data) => {
            return `${data.username} with ${data.games} Games.`
        }
    }
    
### .loadData(url)

Loads data into the list from an url.

    myList.loadData("/api/users")

### .add(data :object)

The data will be passed to the template function which will create the elements with the provided data.

    myList.add({username: "bob123", games: 10})
    
### .addAll(data :array)

The data will be passed to the template function which will create the elements with the provided data.

    myList.add([
        {username: "bob123", games: 10},
        {username: "jeff456", games: 6}
    ])

# class VForm(string | element)

### .json()

Returns a valid json string; Already strinlsgified object.

### .ajax(url, method :string)

Makes any valid AJAX call and returns a parsed JSON object.

    myForm.ajax("/api/users", "GET")
    
### .reset()

Resets / clears the form from previously typed values.