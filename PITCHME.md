## Gem Etiquette

#### John Fearnside
#### jfearnside@avvo.com

---

## `.gemspec` (not `Gemfile`)

---

## Minimize dependencies
- less impact on clients
- `add_development_dependency` is your friend!
- don't require command line tools
- don't require other gems

---

## Don't monkey-patch!

---

## No ActiveSupport!
- invites conflict with Rails apps
- rude to non-Rails apps

---

## Example: `class_attribute`

---

## Example: `xxx`

---

## Opt-in dependencies
- Use *iff* client decides to require

---

## Q & A

---

## Resources
Slides: https://gitpitch.com/jwfearn/slides-gem-etiquette
