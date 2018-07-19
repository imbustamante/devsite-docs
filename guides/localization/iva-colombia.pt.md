---
  sites_supported:
      - mco
      - global
---

# Considerações IVA Colômbia

> NOTE
>
> Nota
>
> Somente para Colômbia.

O IVA (Imposto ao Valor Agregado) é uma carga fiscal que recai sobre a venda de produtos ou a prestação de serviços dentro do território colombiano. Alguns produtos assim como alguns serviços estão excluídos do IVA e outros possuem tarifas reduzidas. Na atualidade, a tarifa geral deste imposto é de 19%.

Para processar corretamente o IVA, permitimos o envio do valor total (transaction_amount), valor líquido (net_amount) e IVA (taxes) no momento de realizar a cobrança através da API.

Neste exemplo te mostramos como enviar os dados:

```curl
curl -X POST \
        -H 'accept: application/json' \
        -H 'content-type: application/json' \
        'https://api.mercadopago.com/v1/payments?access_token=ACCESS_TOKEN' \
        -d '{
                "transaction_amount": 10000,
                "net_amount": 9500,
                "taxes":[{
                        "value": 500,
                        "type": "IVA"
                }],
                "token": "ff8080814c11e237014c1ff593b57b4d",
                "description": "Title of what you are paying for",
                "installments": 1,
                "payment_method_id": "visa",
                "payer": {
                        "email": "test_user_19653727@testuser.com"
                }
        }'
```

O IVA deve ser um valor determinado, não envie uma porcentagem. Caso não envie os atributos _net_amount_ e _taxes_, se aplicará o IVA geral (19%).
