## Тестовое задание
#### Описание
1. Необходимо выполнить поиск по дереву объекта: найти все значения равные единице и вывести их пути нахождения. 
Типами свойств могут быть строки, массивы, числа, а так же вложенные объекты.
2. Выполнить рендеринг первого задания с помощью блочных элементов так, чтобы была видна четкая структура дерева,
закрасить цветом блоки, в которых отрисовываются найденные значения.
3. Выполнить выше перечисленные задания с использованием сборщика модулей Webpack.

#### 1. Поиск указанных значений
    ```javascript
    /* Задание 1: вывод путей свойств дерева со значением '1' */
    function getValue1(tree, curPath = '', prevPath = ''){
        let prop;
        for(prop in tree){
            if(tree[prop] === 1){
                console.log(tree[prop], curPath + prop);
            }

            if(Array.isArray(tree[prop])){
                for(let i = 0; i < tree[prop].length; i++){
                    if(tree[prop][i] === 1) {
                        console.log(tree[prop][i], curPath + i);
                    }
                }

                continue;
            }

            if(typeof(tree[prop]) === 'object'){
                prevPath = curPath;
                curPath += prop + ' > ';
                getValue1(tree[prop], curPath);
                curPath = prevPath;
            }
        }
    }
    ```
