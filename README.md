# Selection_Sort

## Como funciona o método de ordenação de strings com Selection Sort? 

O projeto de ordenação de strings emprega o algoritmo Selection Sort por meio da linguagem C. O Selection Sort é um método algorítimico que consiste em posicionar iterativamente o menor valor do conjunto em análise na primeira posição do vetor, em seguida, o segundo menor valor é colocado na segunda posição, e esse procedimento é reiterado de forma sequencial. A direção da ordenação pode ser ajustada para ser crescente ou decrescente, de acordo com a intenção do usuário. No presente contexto, a ordenação das strings é realizada na sequência que vai do valor mais baixo ao mais alto. 

```c
  void func_ordena(Funcionario **func, int count)
{
    int i, primeiroID, j;
    Funcionario *valor_teste;

    for (i = 0; i < count; i++)
    {

        valor_teste = func[i]; 

        primeiroID = i;
        for (j = i + 1; j < count; j++)
        {
            if (func_compara(func[primeiroID]->nome, func[j]->nome) == 1)
            {
                primeiroID = j;
            }
        }

        if (primeiroID != i)
        {
            func[i] = func[primeiroID];
            func[primeiroID] = valor_teste;
        }
    }
}

```
## Complexidade de Espaço do Selection Sort

A complexidade de espaço de um algoritmo, S(P), é a análise do espaço de memória requerido para a sua execução, que consiste tanto a parte fixa quanto a parte variável do espaço. 

No Selection Sort, a parte fixa consiste nas quatro variáveis do tipo `int`, que ocupam 4 Bytes de memória cada, e o ponteiro para a struct Funcionário, que possui 84 Bytes, considerando o tamanho de todos os parâmetros juntos. Totalizando 100 Bytes fixos.

E a parte variável, consiste no vetor de ponteiros para a struct Funcionário, que irá ocupar o equivalente a n*84, sendo n o número de entrada da variável `count`.

Dessa forma, o Selection Sort possui complexidade espacial de

$$
S(P) = (n*84 + 100) Bytes
$$


$$
S(P) = 
$$

## Complexidade de Tempo do Selection Sort

A complexidade de tempo de um algoritmo, T(n), é a análise do tempo de execução do mesmo. O Selection Sort possui complexidade

$$ 
T(n) = O (n^2) 
$$

```c
  void func_ordena(Funcionario **func, int count)
{
    int i, primeiroID, j; // c1
    Funcionario *valor_teste; // c2

    for (i = 0; i < count; i++) // c3*n
    {

        valor_teste = func[i]; // c4*n

        primeiroID = i; // c4*n
        for (j = i + 1; j < count; j++) //c5*n*(n-1)/2
        {
            if (func_compara(func[primeiroID]->nome, func[j]->nome) == 1) // c6*n*(n-1)/2
            {
                primeiroID = j; // c7*n*(n-1)
            }
        }

        if (primeiroID != i) // c8*n
        {
            func[i] = func[primeiroID]; // c9*n
            func[primeiroID] = valor_teste; // c10*n
        }
    }
}

```
Os termos constantes foram nomeados como a, b os termos que acompanham (n) e c os termos que acompanham [n*(n-1)/2]

$$T(n) = O(a + b*n + c*(n^2-n)/2)$$

$$T(n) = O(n^2)$$

## Exemplificando o funcionamento do Selection Sort 
<p align="center">
 <img src="selection-sort-animation.gif"/>
</p>
