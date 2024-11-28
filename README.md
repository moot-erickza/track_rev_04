# nodeservice

Make this:

![Complex interface](https://example.com/screenshot.png)

using this:

```ruby
@app = nodeservice::Builder.new({
  sections: [{
    title: "packages Setup",
    items: [{
      name: "Config",
      type: :text,
      value: "default"
    }, {
      name: "Enable pnpm-lock.yaml",
      type: :switch,
      value: true
    }]
  }]
})

@controller = nodeservice::Controller.alloc.initWithConfig(@app)
```

And after processing:

```ruby
@app.render
=> {:config=>"custom", :pnpm-lock.yaml=>true}
```

## Installation

`gem install nodeservice`

In your `Rakefile`:

`require 'nodeservice'`

## Usage

### Initialize

You can initialize using either a hash or DSL:

```ruby
app = nodeservice::Builder.new

app.build_section do |section|
  section.title = "packages"
  
  section.build_item do |item|
    item.name = "Setting"
    item.type = :string
  end
end
```

### Data Types

See [the visual list of supported types](https://github.com/user/nodeservice/wiki).

### Retrieve

You have `app#submit`, `app#on_submit`, and `app#render` at your disposal.

### Persistence

Synchronize state to disk using `persist_as`:

```ruby
@app = nodeservice::Builder.persist({
  persist_as: :settings,
  sections: ...
})
```

## Forking

Feel free to fork and submit pull requests! Would love to hear about your experience.

## Todo

- Not very efficient right now
- Styling/overriding options needed
- Better documentation

