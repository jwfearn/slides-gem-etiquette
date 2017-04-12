## Gem Etiquette

#### John Fearnside
#### jfearnside@avvo.com

---

Being polite to your clients

---

## `.gemspec` (not `Gemfile`)

---

## Cleanup generated files
- remove tutorial comments
- remove unneeded code
- fix any `gem build` warnings
- replace `.files`

---

## Simple, minimal `.files`
- `bundle gem mygem --test=rspec --no-coc --no-exe --mit`
- `%x{git ls-files -z}.split("\x0")` # only version controlled files
  spec.files = repo_files
    .reject { |f| f.match(%r{^(test|spec|features)/}) } # directories
    .reject { |f| f.match(%r{.*\.(gem|lock)}) } # file extensions
    .reject { |f| f.match(%r{(Rakefile)}) } # files
- Don't add `Gemfile.lock` to version control...
- ...or ignore it

  repo_files = `git ls-files -z`.split("\x0")
  spec.files = repo_files
    .reject { |f| f.match(%r{^(bin|test|vendor)/}) }
    .reject { |f| f.match(%r{\.(lock)$}) }
    .reject { |f| f.match(%r{(circle\.yml|Rakefile)}) }

  spec.files = Dir.glob %w[
    Gemfile
    README.md
    lib/**/*
  ]

---



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

## Example: `parameterize`

---

## Example: `delegate`
- gratutitous!
- use built-in Forwardable

---

## Opt-in dependencies
- Use *iff* client decides to require

      def with_clipboard_class
        gem "clipboard", "~> 1.0"
        require "clipboard"
        yield Clipboard
      rescue LoadError
        # do nothing
      end

      def foo(short_url)
        with_clipboard_class do |clipboard_class|
          clipboard_class.copy(short_url)
          puts "URL has also been copied to the clipboard."
        end
      end

---

## Q & A

---

## Resources
https://gitpitch.com/jwfearn/slides-gem-etiquette
https://www.rubytapas.com/2012/10/05/episode-006-forwardable/

