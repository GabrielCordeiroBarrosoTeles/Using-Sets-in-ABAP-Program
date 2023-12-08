# Using Sets in ABAP Program

Aqui estão os exemplos em português, com comentários explicativos:

### Criando um Conjunto Básico:

Um conjunto básico é uma simples coleção de valores. No exemplo abaixo, vamos criar um conjunto básico e adicionar valores a ele.

```ABAP
DATA: conjunto_basico TYPE TABLE OF rgsb4,
      nome_conjunto   TYPE rgsb4-setname,
      valor           TYPE rgsb4-value.

" Defina o nome do conjunto básico
nome_conjunto = 'ZSET_BASICO'.

" Adicione valores ao conjunto
valor = 'VALOR1'.
APPEND VALUE #( setname = nome_conjunto value = valor ) TO conjunto_basico.

valor = 'VALOR2'.
APPEND VALUE #( setname = nome_conjunto value = valor ) TO conjunto_basico.

" Chame a função para inserir o conjunto
CALL FUNCTION 'S_SET_INSERT'
  EXPORTING
    setname = nome_conjunto
  TABLES
    values  = conjunto_basico.

IF sy-subrc = 0.
  WRITE: / 'Conjunto Básico criado com sucesso.'.
ELSE.
  WRITE: / 'Erro ao criar Conjunto Básico.'.
ENDIF.
```

### Criando um Conjunto Unidimensional:

Um conjunto unidimensional é semelhante a um conjunto básico, mas pode ter múltiplos valores para cada entrada.

```ABAP
DATA: conjunto_unidimensional TYPE TABLE OF rgsb4,
      nome_conjunto_uni      TYPE rgsb4-setname,
      valor                   TYPE rgsb4-value,
      identificador           TYPE rgsb4-id.

" Defina o nome do conjunto unidimensional
nome_conjunto_uni = 'ZSET_UNIDIMENSIONAL'.

" Adicione valores ao conjunto unidimensional
valor = 'VALOR1'.
identificador = 'ID1'.
APPEND VALUE #( setname = nome_conjunto_uni id = identificador value = valor ) TO conjunto_unidimensional.

valor = 'VALOR2'.
identificador = 'ID2'.
APPEND VALUE #( setname = nome_conjunto_uni id = identificador value = valor ) TO conjunto_unidimensional.

" Chame a função para inserir o conjunto unidimensional
CALL FUNCTION 'S_SET_INSERT'
  EXPORTING
    setname = nome_conjunto_uni
  TABLES
    values  = conjunto_unidimensional.

IF sy-subrc = 0.
  WRITE: / 'Conjunto Unidimensional criado com sucesso.'.
ELSE.
  WRITE: / 'Erro ao criar Conjunto Unidimensional.'.
ENDIF.
```

### Excluindo um Conjunto:

Para excluir um conjunto, você pode usar o módulo de função `S_SET_DELETE`.

```ABAP
DATA: nome_conjunto TYPE rgsb4-setname.

" Defina o nome do conjunto a ser excluído
nome_conjunto = 'ZSET_BASICO'. "Substitua pelo nome do seu conjunto.

" Chame a função para excluir o conjunto
CALL FUNCTION 'S_SET_DELETE'
  EXPORTING
    setname = nome_conjunto.

IF sy-subrc = 0.
  WRITE: / 'Conjunto excluído com sucesso.'.
ELSE.
  WRITE: / 'Erro ao excluir o conjunto.'.
ENDIF.
```

Certifique-se de substituir os nomes dos conjuntos ('ZSET_BASICO', 'ZSET_UNIDIMENSIONAL') pelos nomes que você deseja usar. Além disso, manipule os erros adequadamente com base nos requisitos de sua aplicação.
