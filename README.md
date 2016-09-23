# 9web.github.io
https://9web.github.io/
> :warning:
  This theme requires ruby and rubygems installed

---

### Start in 6 steps

1. clone: git clone -b gh-blog https://github.com/9web/9web.github.io.git
2. Enter the folder: `cd 9web.github.io/`
3. install Ruby and RubyDevKit: `http://rubyinstaller.org/downloads/`
   （make sure the version consistent）
4. install jekyll: $gem install jekyll
5. install Bundle: $gem install bundle 
    $ bundle install
6. Start Jekyll server: `jekyll serve`

Access, [localhost:4000](http://localhost:4000/)

### publish posts in Github pages in 3 steps

1. pull repo `https://github.com/9web/9web.github.io.git`            (branch: gh-blog)
2. add yourself post to the posts file and then updata the github    (branch: gh-blog)
3. Run `rake` or `rake publish` for build and publish on Github

---

### Using Rake tasks

* Create a new page: `rake page name="contact.md"`
* Create a new post: `rake post title="TITLE OF THE POST"`

---


