# easynvest-api &middot; doc

[![GitHub license](https://img.shields.io/badge/license-MIT-blue.svg)](https://github.com/facebook/react/blob/master/LICENSE)

Objective to this is to start to document on how onw can we use easynvest XHR calls and turn its structure in an api that should be able to:
* **Market Data Retrieve:** Retrieve current price, current volumes and market depth.
* **Execute on order:** Send order eletronicaly to the broker on buy and sell positions.

## Market Data Retrieve

You need two base parameters ``c=123456`` that inforns your easynvent account and ``q=PETR4,27,0`` that informs what is the the ticket that you will like to retrieve data from and what is the level of the data.
  ```curl
  curl "https://mdgateway.easynvest.com.br/iwg/snapshot/?t=webgateway&c=123456&q=PETR4,29,0,10"
  ```
  
Data retrieved is in a json format and could be simplified by doing ``q=PETR4,1,0,0`` that would remove from the data the ``Ts`` and ``BBP``content.
* **Ts:** Contains data from broker trading for that ticker: 
  ```json
  {
      "broker_code_that_bought": "Br",
      "broker_code_that_sold": "Sr",
      "Quantity": "Q",
      "Price": "P",
      "to_be_investigated": "NCFPD",
      "transaction_time": "DT"
  }
  ```
  
* **BBP:** Presents data from all offers and its a representation of the market depth. Data is divided in two blocks Bd = "Bid" (COMPRA) and A; = "Ask" (VENDA).
  ```json
  {
      "Time_order_input": "DT",
      "Price": "P",
      "Qunatity": "Q",
      "Broker_code": "B"
  }
  ```
  
  


## Here is the full curl results for reference using ``PETR4,29,0,10``

```json
{
    "_meta": {},
    "Value": [
        {
            "S": "PETR4",
            "UT": "2020-06-08T17:59:58.797",
            "Ts": [
                {
                    "Br": "21",
                    "Sr": "308",
                    "Q": 200,
                    "P": 22.5,
                    "NCFPD": 0.4,
                    "DT": "2020-06-08T17:59:57.02"
                },
                {
                    "Br": "107",
                    "Sr": "308",
                    "Q": 200,
                    "P": 22.5,
                    "NCFPD": 0.4,
                    "DT": "2020-06-08T17:59:56.432"
                },
                {
                    "Br": "21",
                    "Sr": "308",
                    "Q": 400,
                    "P": 22.5,
                    "NCFPD": 0.4,
                    "DT": "2020-06-08T17:59:53.743"
                },
                {
                    "Br": "21",
                    "Sr": "3",
                    "Q": 200,
                    "P": 22.5,
                    "NCFPD": 0.4,
                    "DT": "2020-06-08T17:59:53.743"
                },
                {
                    "Br": "21",
                    "Sr": "3",
                    "Q": 200,
                    "P": 22.48,
                    "NCFPD": 0.38,
                    "DT": "2020-06-08T17:59:53.55"
                },
                {
                    "Br": "21",
                    "Sr": "3",
                    "Q": 200,
                    "P": 22.48,
                    "NCFPD": 0.38,
                    "DT": "2020-06-08T17:59:52.566"
                },
                {
                    "Br": "21",
                    "Sr": "308",
                    "Q": 100,
                    "P": 22.48,
                    "NCFPD": 0.38,
                    "DT": "2020-06-08T17:59:51.691"
                },
                {
                    "Br": "21",
                    "Sr": "21",
                    "Q": 400,
                    "P": 22.48,
                    "NCFPD": 0.38,
                    "DT": "2020-06-08T17:59:51.69"
                },
                {
                    "Br": "308",
                    "Sr": "21",
                    "Q": 600,
                    "P": 22.48,
                    "NCFPD": 0.38,
                    "DT": "2020-06-08T17:59:51.69"
                },
                {
                    "Br": "120",
                    "Sr": "21",
                    "Q": 100,
                    "P": 22.49,
                    "NCFPD": 0.39,
                    "DT": "2020-06-08T17:59:51.69"
                },
                {
                    "Br": "308",
                    "Sr": "21",
                    "Q": 1000,
                    "P": 22.49,
                    "NCFPD": 0.39,
                    "DT": "2020-06-08T17:59:51.69"
                },
                {
                    "Br": "39",
                    "Sr": "21",
                    "Q": 1000,
                    "P": 22.49,
                    "NCFPD": 0.39,
                    "DT": "2020-06-08T17:59:51.69"
                },
                {
                    "Br": "3",
                    "Sr": "21",
                    "Q": 300,
                    "P": 22.49,
                    "NCFPD": 0.39,
                    "DT": "2020-06-08T17:59:51.69"
                },
                {
                    "Br": "90",
                    "Sr": "21",
                    "Q": 600,
                    "P": 22.49,
                    "NCFPD": 0.39,
                    "DT": "2020-06-08T17:59:51.69"
                },
                {
                    "Br": "107",
                    "Sr": "3",
                    "Q": 1000,
                    "P": 22.5,
                    "NCFPD": 0.4,
                    "DT": "2020-06-08T17:59:50.206"
                },
                {
                    "Br": "3",
                    "Sr": "3",
                    "Q": 2000,
                    "P": 22.5,
                    "NCFPD": 0.4,
                    "DT": "2020-06-08T17:59:49.502"
                },
                {
                    "Br": "1982",
                    "Sr": "3",
                    "Q": 100,
                    "P": 22.5,
                    "NCFPD": 0.4,
                    "DT": "2020-06-08T17:59:49.2"
                },
                {
                    "Br": "3",
                    "Sr": "3",
                    "Q": 5400,
                    "P": 22.5,
                    "NCFPD": 0.4,
                    "DT": "2020-06-08T17:59:45.156"
                },
                {
                    "Br": "90",
                    "Sr": "386",
                    "Q": 200,
                    "P": 22.49,
                    "NCFPD": 0.39,
                    "DT": "2020-06-08T17:59:42.256"
                },
                {
                    "Br": "107",
                    "Sr": "3",
                    "Q": 400,
                    "P": 22.5,
                    "NCFPD": 0.4,
                    "DT": "2020-06-08T17:59:39.391"
                },
                {
                    "Br": "1099",
                    "Sr": "3",
                    "Q": 200,
                    "P": 22.5,
                    "NCFPD": 0.4,
                    "DT": "2020-06-08T17:59:36.664"
                },
                {
                    "Br": "15",
                    "Sr": "3",
                    "Q": 400,
                    "P": 22.5,
                    "NCFPD": 0.4,
                    "DT": "2020-06-08T17:59:36.664"
                },
                {
                    "Br": "308",
                    "Sr": "3",
                    "Q": 100,
                    "P": 22.5,
                    "NCFPD": 0.4,
                    "DT": "2020-06-08T17:59:36.664"
                },
                {
                    "Br": "735",
                    "Sr": "3",
                    "Q": 4500,
                    "P": 22.5,
                    "NCFPD": 0.4,
                    "DT": "2020-06-08T17:59:36.664"
                },
                {
                    "Br": "735",
                    "Sr": "308",
                    "Q": 100,
                    "P": 22.5,
                    "NCFPD": 0.4,
                    "DT": "2020-06-08T17:59:35.685"
                }
            ],
            "Ps": {
                "AM": "false",
                "AP": "22.5",
                "AS": "1100",
                "A": "PETR",
                "BP": "22.48",
                "BS": "100",
                "CC": "EPNNPR",
                "CP": "22.1",
                "CM": "1",
                "CSM": "999912",
                "CAEI": "196",
                "COI": "BR",
                "C": "BRL",
                "GI": "N2",
                "I": "BRPETRACNPR6",
                "ID": "20191227",
                "MSI": "82",
                "MD": "99991231",
                "MMY": "999912",
                "MOQ": "56020428",
                "MnOQ": "100",
                "MPI": "0.01",
                "PD": "1",
                "Pt": "5",
                "SD": "PETROBRAS   PN      N2",
                "SE": "BVMF",
                "SEAN": "XBSP",
                "SG": "10",
                "SI": "200000355262",
                "SIS": "8",
                "SST": "1004",
                "STS": "101",
                "STSD": "final",
                "ST": "PS",
                "SUA": "M",
                "SVT": "99991231235959000",
                "StC": "BRL",
                "StD": "99991231",
                "StT": "D2",
                "S": "PETR4",
                "TSD": "2",
                "TSOT": "",
                "TSSI": "18",
                "__feederId": "053",
                "TOQ": "",
                "TOP": "",
                "TNC": "",
                "TNCP": "",
                "LTD": "20200608",
                "LTT": "175957020",
                "LTDT": "20200608175957020",
                "NCPD": "0.4",
                "NCPDP": "1.81",
                "TT": "82444400",
                "P": "22.5",
                "TC": "78275",
                "TD": "1",
                "LTS": "200",
                "OP": "22.55",
                "MxP": "22.59",
                "MnP": "22.01",
                "AvP": "22.31",
                "V": "1839883511.00"
            },
            "Bk": {
                "Bd": [
                    {
                        "DT": "2020-06-08T17:59:53.55",
                        "P": 22.48,
                        "Q": 100,
                        "B": "21"
                    },
                    {
                        "DT": "2020-06-08T16:55:00.024",
                        "P": 0,
                        "Q": 900,
                        "B": "3"
                    },
                    {
                        "DT": "2020-06-08T16:55:00.024",
                        "P": 0,
                        "Q": 3000,
                        "B": "3"
                    },
                    {
                        "DT": "2020-06-08T16:55:00.024",
                        "P": 0,
                        "Q": 700,
                        "B": "3"
                    },
                    {
                        "DT": "2020-06-08T16:55:00.024",
                        "P": 0,
                        "Q": 400,
                        "B": "3"
                    },
                    {
                        "DT": "2020-06-08T16:55:00.024",
                        "P": 0,
                        "Q": 200,
                        "B": "3"
                    },
                    {
                        "DT": "2020-06-08T16:55:00.024",
                        "P": 0,
                        "Q": 900,
                        "B": "3"
                    },
                    {
                        "DT": "2020-06-08T16:55:00.024",
                        "P": 0,
                        "Q": 2200,
                        "B": "3"
                    },
                    {
                        "DT": "2020-06-08T16:55:00.024",
                        "P": 0,
                        "Q": 1900,
                        "B": "3"
                    },
                    {
                        "DT": "2020-06-08T16:55:00.024",
                        "P": 0,
                        "Q": 400,
                        "B": "3"
                    }
                ],
                "Ak": [
                    {
                        "DT": "2020-06-08T17:59:51.329",
                        "P": 22.5,
                        "Q": 100,
                        "B": "386"
                    },
                    {
                        "DT": "2020-06-08T17:59:53.554",
                        "P": 22.5,
                        "Q": 1000,
                        "B": "114"
                    },
                    {
                        "DT": "2020-06-08T17:59:32.869",
                        "P": 22.51,
                        "Q": 400,
                        "B": "85"
                    },
                    {
                        "DT": "2020-06-08T17:59:55.767",
                        "P": 22.51,
                        "Q": 1000,
                        "B": "21"
                    },
                    {
                        "DT": "2020-06-08T17:59:04.012",
                        "P": 22.52,
                        "Q": 100,
                        "B": "27"
                    },
                    {
                        "DT": "2020-06-08T17:58:26.473",
                        "P": 22.52,
                        "Q": 200,
                        "B": "1099"
                    },
                    {
                        "DT": "2020-06-08T17:58:36.609",
                        "P": 22.52,
                        "Q": 1000,
                        "B": "3"
                    },
                    {
                        "DT": "2020-06-08T17:59:48.398",
                        "P": 22.52,
                        "Q": 500,
                        "B": "308"
                    },
                    {
                        "DT": "2020-06-08T17:59:58.797",
                        "P": 22.52,
                        "Q": 4000,
                        "B": "386"
                    },
                    {
                        "DT": "2020-06-08T17:51:23.426",
                        "P": 22.53,
                        "Q": 500,
                        "B": "15"
                    }
                ]
            },
            "BBP": null,
            "HL": {}
        }
    ]
}
```
 
## Execute on order

Executing an order is a little bit different and would require more analysis on how to make this work properly.

```
curl -d "Ativo=PETR4&Quantidade=100&Preco=22%2C50&Ordem=2&Validade=Dia&AssinaturaEletronica=SECRET&GravarAssinaturaEletronica=false&Operacao=1" -X POST https://hb3.easynvest.com.br/ordem/enviarordem/ -H "Cookie: <cookieHere>" 
```

The parameters that must be passed to the curl reques are:
```json
{
    "Ativo": "PETR4",
    "Quantidade": "100",
    "Preco": "22.50",
    "Ordem": "2",
    "Validade": "Dia",
    "AssinaturaEletronica": "SECRET",
    "GravarAssinaturaEletronica": "false",
    "Operacao": "1"
}
```
```Operacao = 1 (Buy)``` and ```Operacao = 2 (Sell)``` 

Please note that in order for that to work you would need to have the cookie from your loged in session from easynvest and also you will need to pass your ```AssinaturaEletronica``` to the request.

This is not a very good way of doing this and it would be much better to have the broker oferring a proper REST API endpoint that we could connect and execute - for know this is a "hack" that can get you up and running in etrading with what they current offer.
