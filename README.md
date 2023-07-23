# swisstreehouse.github.io

Visit: https://swisstreehouse.ch/

## Prepare images:

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

## Preview the page locally:

Preview the page:
```
docker run -it --rm -v "$PWD":/usr/src/app -w /usr/src/app -p 4000:4000 ruby:2.7 sh -c "bundle install && bundle exec jekyll serve --host 0.0.0.0"
```

It will then be available under http://localhost:4000

Note: Jerkyll does not work with Ruby 3.0 as of 23.07.2023
