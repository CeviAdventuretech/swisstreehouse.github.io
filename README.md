# cevimail.github.io

Visit: https://swisstreehouse.ch

## Build the page locally:

Setup ruby 2.7:
```
curl -L get.rvm.io > rvm-install
bash < ./rvm-install
rvm install 2.7.0
rvm use 2.7.0
```

Prepare images:
```
find . -depth -name "*.JPG" -exec sh -c '
    from="JPG"
    to="jpg"
    shift 2
    for pathname do
        mv "$pathname" "${pathname%.$from}.$to"
    done' sh "$1" "$2" {} +

mkdir -p assets/images/how_we_built_it/thumbs
mogrify -path assets/images/how_we_built_it/thumbs -quality 90 -resize 200x200^ assets/images/how_we_built_it/*.jpg
```

Build a page:
```
bundle install
bundle exec jekyll serve
```

Not Jerkyll does not work with Ruby 3.0 as of 28.09.2021

It will then be available under http://localhost:4000
