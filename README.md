
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
### Sum
```
sha256sum bash-it-my_local_changes-20220709-9a500059.diff
a7ef77531453232c4288b1bf81e00845d953efae88642ac7b2c36398f9f9a52b  bash-it-my_local_changes-20220709-9a500059.diff


for f in *.diff; do echo;
    sha256sum $f |
    sed 's@\(.\+\)  \(.\+\.diff\)@url "https://raw.githubusercontent.com/lopesivan/my_patches/main/bash-it/\2"\nsha256 "\1"@';
done

```

### Aplicando patch
```
patch -Np1 -i ../bash-it-my_local_changes-20220709-9a500059.diff

```

