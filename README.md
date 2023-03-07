# Resolving references bug

Reference to `person.yml#/components/schemas/person` in `demo/household/address.yml` doesn't recognize correctly.

## Attempt #1

1. Run `datamodel-codegen --input demo/ --output model.py`
2. Got `FileNotFoundError: [Errno 2] No such file or directory: '.../demo/person.yml'`

## Attempt #2

1. Change ref in `demo/household/address.yml` to `household/person.yml#/components/schemas/person`
2. Run `datamodel-codegen --input demo/ --output model.py`
3. Got `FileNotFoundError: [Errno 2] No such file or directory: '.../demo/household/household/person.yml'`

## Attempt #3

1. Change ref in `demo/household/address.yml` to `../household/person.yml#/components/schemas/person`
2. Run `datamodel-codegen --input demo/ --output model.py`
3. Got `FileNotFoundError: [Errno 2] No such file or directory: '.../demo/../household/person.yml'`
