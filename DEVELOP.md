
```shell
# install development requirements
pip install -r dev-requirements.txt

# test (with docker as default)
molecule test


# test with incus
molecule test --scenario-name=incus

```