## Gem Etiquette
### Tips for Making Polite Ruby Libraries

#### John Fearnside
#### jfearnside@avvo.com

---

Being polite to your clients

---

Don't burden them with:
- dependencies
- confusion
- baggage
- surprises

---

## Minimize dependencies
- less impact on clients
- `add_development_dependency` is your friend!
- don't shell out to command line tools
- don't require other gems

---

## Don't monkey-patch!

---

## No ActiveSupport!
- monkey-patch city
- invites conflict with Rails apps
- rude to non-Rails apps
- not needed (use pure Ruby instead)

---

Examples:

| ActiveSupport     | Ruby                    |
| ----------------- | ----------------------- |
| `delegate`        | `Forwardable`           |
| `class_attribute` | class instance variable |

---

## Approach
+ Start with scaffolding
+ Remove code/warnings
+ Tidy up what's left
+ Add code

---

## Scaffolding
```
bundle gem mygem --test=rspec --no-coc --no-exe --no-ext --mit
cd mygem
bundle install
bundle exec rspec
```
---

## Warnings
- Replace placeholder summary
- Remove `spec.description`

---

## Remove
- private gemserver section
- spec.bindir
- spec.executables

---

## Tidy up
- Normal quotes
- Glob for spec.files
- Replace placeholder homepage
- Remove tutorial comments

---

Don't add `Gemfile.lock` to version control

---

Gemspec
- Use `.gemspec` file
- minimal Gemfile:
```ruby
source "https://rubygems.org"
gemspec
```

---

## Simple Files
- scaffolding too complicated
- use this instead:
```
   spec.files = Dir.glob %w[
    Gemfile
    README.md
    lib/**/*
  ]
```

---

## Q & A

---

## Resources
https://gitpitch.com/jwfearn/slides-gem-etiquette
https://www.rubytapas.com/2012/10/05/episode-006-forwardable/

