
# Meus patches

## Criando um patche

### Clonando o repositório
```bash
git clone repositório
```

### Modificando o repositório

.. Aplicando as modificações ..


### Gerando o diff
```bash
git checkout -b doing
git ci -a
git format-patch --stdout HEAD^ >  ../st-$(git log -n1 --format=format:"%s"| tr '[[:upper:] ]' '[[:lower:]_]')-$(date +%Y%m%d)-$(git log -n1 --format=format:"%h").diff
git checkout master
git branch -D doing
```

