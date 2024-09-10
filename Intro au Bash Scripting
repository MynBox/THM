### Ressources

- https://devhints.io/bash
- https://www.codewars.com/
- https://www.hackerrank.com/

L'utilisation du shebang `#!/bin/bash` est une bonne pratique pour tous vos scripts Bash. Elle garantit que votre script sera interprété par Bash, quel que soit l'environnement, rendant ainsi vos scripts plus robustes et portables.

#!/bin/bash

`echo` est l’équivalent de `print`

### Les variables

Pour créer une variable, on va spécifier le nom de la variable, l’opérateur d’affection et la valeur a stocké.

Pour l’utiliser on met le signe “$”suivi de la variable

```bash
name=”W@ffl3”
echo $name
```

set -x et set +x nous permet de debbuger notre script

### Les paramètres

```bash
name=$1
echo $name
./example.sh W@ffl3
#Ca va afficher :
W@ffl3
```

- On précise quel input prendre

```bash
name=$2
echo $name
./example.sh W@ffl3 Kulina
#Ca va afficher :
Kulina
```

**Utiliser un input dans un script.**

```bash
#!/bin/bash
echo "Quel est ton prénom ?"
read name
echo "Ton nom est $name"
```

- Le read est équivalent à un name = input()

**1. Obtenir le Nombre d'Arguments Fourni à un Script**

Vous pouvez utiliser la variable spéciale `$#` pour obtenir le nombre d'arguments fournis à un script.

```bash
#!/bin/bash
echo "Nombre d'arguments fournis : $#"

```

**2. Obtenir le Nom du Fichier du Script Actuel (c'est-à-dire le Premier Argument)**

Le nom du fichier du script actuel est stocké dans la variable spéciale `$0`.

```bash
#!/bin/bash
echo "Le nom du fichier du script actuel : $0"

```

**3. Obtenir le 4ème Argument Fourni au Script**

Vous pouvez accéder au 4ème argument en utilisant le paramètre positionnel `$4`.

```bash
#!/bin/bash
echo "Le 4ème argument fourni au script : $4"
```

### Array

`transport=('car' 'train' 'bike' 'bus')`

- Contrairement à Python, on ne doit pas séparer les élements par des “,” mais par des espaces.

```bash
echo ${transport[@]}
echo "${transport[1]}"
transport[1]='trainride'
unset transport[1]
```

- `@` prend tous les éléments.
- La deuxième commande renvoie “train”.
- Cette commande remplace l’élément indexer.
- `unset` : nous permet d’enlever un élément.

### Conditionnels

```bash
#!/bin/bash
filename=$1
if [ -f "$filename" ] && [ -w "$filename" ]
then
echo "hello" > $filename
else
touch "$filename"
echo "hello" > $filename
fi
```

- La structure pour utiliser les conditionnels est un peu différente de Python.
- On écrit `if` suivi de la condition à vérifier entre crochets
- Il faut laisser un petit espace entre les crochets et les autres caractères.
- On passe à la ligne et on écrit `then` et on repasse à la ligne pour écrire ce qu’il doit se passer lorsque la condition est vérifié ou non.
- il faut fermer notre condition avec `fi` à la fin.
- -f c’est pour un fichier donc pour vérifier si c’est un répertoire ce sera -d
- pour savoir si on peut écrire dedans c’est -w et donc pour lire ce sera -r

| **Operator** | **Description** |
| --- | --- |
| -eq | Checks if the value of two operands are equal or not; if yes, then the condition becomes true. |
| -ne | Checks if the value of two operands are equal or not; if values are not equal, then the condition becomes true. |
| -gt | Checks if the value of left operand is greater than the value of right operand; if yes, then the condition becomes true. |
| -lt | Checks if the value of left operand is less than the value of right operand; if yes, then the condition becomes true. |
| -ge | Checks if the value of left operand is greater than or equal to the value of right operand; if yes, then the condition becomes true. |
