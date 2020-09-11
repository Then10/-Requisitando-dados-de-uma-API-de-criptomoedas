<!DOCTYPE html>
<html>
    <head>
        <title>CoinMarketCap</title>
        <Link rel="stylesheet" type="text/css"
        href="https://stackpath.bootstrapcdn.com/bootstrap/4.5.2/css/bootstrap.min.css"
        <meta charset="Utf-8">
          </head>
        <body>
            <nav aria-label="breadcrumb">
                <ol class="breadcrumb">
                  <li class="breadcrumb-item active" aria-current="page">Coin Market Cap</li>
                </ol>
              </nav>
            
              <div class="d-flex p-3 bd-highlight">
                <div id='coins'></div>
              </div>]


            <script type="text/javascript">
            //My api key
            var apikey = {
                key: 'COLE AQUI SUA API KEY:)'

            }

            // GET Fetch Requisition
            fetch('https://pro-api.coinmarketcap.com/v1/criptocurrency/map?CMC_PRO_API_KEY=' + 
            apikey.key)
            .then((response) => {
                if(!response.ok) throw new error('Erro ao executar a requisição, status' + response.status);
                return response.json();
            })
            .then ((api) => {

                var texto = "";
                // get 15 coins and symbols
                for(let i = 0; i < 15; i++){


                    // Show API information 

                    texto = texto + `

                    <div class="media">
                    <img src="coin.jpg" class="align-self-center mr-3" alt="coin" width="100" height="60">
                    <div class="media-body">
                        <h5 class="mt-2">${api.data[i].name}</h5>
                        <p>${api.data[i].symbol}</p>
                        </div>
                    </div>
                    
                    `;

                    document.getElementById("coins").innerHTML = texto;

                }
            })
            .catch((error) => {
                console.error(error.message);
            });
        </script> 
        </body>
</html>
