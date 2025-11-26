[![Github Pages](https://img.shields.io/badge/github%20pages-121013?style=for-the-badge&logo=github&logoColor=white)](https://sfu-dhil.github.io/dhil-projects/)

# dhil-projects


## Build objects (generate_derivatives)

    docker run --rm -it --platform linux/amd64  \
        -v ${PWD}/app/objects:/app/objects \
        ghcr.io/sfu-dhil/collectionbuilder-docker rake generate_derivatives


## Build for deployment

    docker run --rm -it --platform linux/amd64  \
        -e METADATA_FILE_URL="https://docs.google.com/spreadsheets/d/e/2PACX-1vQ1w2oAELCjCt6BbEVv2UmRBOQ7OOXAZHHZLTwjlAQKUDKFHsGy4I9Eq1pp6a4lqTYrAvttEYjW75f_/pub?gid=0&single=true&output=csv" \
        -v ${PWD}/app/_data:/app/_data \
        -v ${PWD}/app/objects:/app/objects \
        -v ${PWD}/app/pages:/app/pages \
        -v ${PWD}/app/_config.yml:/app/_config.yml \
        -v ${PWD}/app/_includes/footer.html:/app/_includes/footer.html \
        -v ${PWD}/app/_includes/item/citation-box.html:/app/_includes/item/citation-box.html \
        -v ${PWD}/app/_includes/item/child/citation-box.html:/app/_includes/item/child/citation-box.html
        -v ${PWD}/app/_includes/item/rights-box.html:/app/_includes/item/rights-box.html \
        -v ${PWD}/app/_layouts/home-infographic.html:/app/_layouts/home-infographic.html \
        -v ${PWD}/_site:/app/_site \
        ghcr.io/sfu-dhil/collectionbuilder-docker rake deploy
