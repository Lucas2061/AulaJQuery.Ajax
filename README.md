# AulaJQuery.Ajax
Utilizando JQuery e Ajax
<!DOCTYPE html>
<html lang="pt-br">
<head>
      <meta charset="utf-8" />
      <title>Minha Página</title>
      <script type="text/javascript" src="jquery.min.js"></script>
      <script type="text/javascript" src="js/main.js"></script>
      <link rel="stylesheet" type="text/css" href="bootstrap-5.1.1-dist/css/bootstrap.min.css">
</head>
<body>

      <nav class="navbar navbar-dark bg-dark">
            <a class="navbar-brand text-whit">Consultar CEP</a>
            <div class="form-inline my-2 my-lg-0">
                <input class="form-control me-2" type="search" placeholder="cep" id="cep">    
               <button class="btn-outline-success my-2 my-sm-0" onclick="consultarCEP()">Bucar</button>
            </div>
          </nav>
          
          <div class="container barra-progresso" style="margin-top: 80px;"> 
          <div class="progress">
             <div class="progress-bar progress-bar-striped progress-bar-animated" role="progressbar" aria-valuenow="75" aria-valuemin="0" aria-valuemax="100" style="width: 100%"></div>
          </div>
      </div>

          <div class="container cep" style="margin-top:20px;">
                <div class="row">
                   <h3 id="titulo_cep">CEP</h3>   
                </div>
                <div class="row" style="margin: 20px;">
                  <table class="table">
                      <tbody>
                            <tr>
                              <td>logradouro</td>
                              <td id="logradouro"></td>
                            </tr>
                            <tr>
                                  <td>bairro</td>
                                  <td id="bairro"></td>
                            </tr>
                            <tr>
                                  <td>localidade</td>
                                  <td id="localidade"></td>
                            </tr>
                            <tr>
                                  <td>UF</td>
                                  <td id="uf"></td>
                            </tr>
                      </tbody>
                  </table>  
                </div>
          </div>
             

</body>
</html>

### MAIN.JS ###


function consultarCEP(){
    $(".barra-progresso").show();
    var cep = document.getElementById("cep").value;
    var url = "https://viacep.com.br/ws/" + cep + "/json/";
    console.log(url)
   $.ajax({
       url: "https://viacep.com.br/ws/01001-000/json/",
       type: "GET",
       success: function(response){
           console.log(response); 
           $("#logradouro").html(response.logradouro);
           $("#bairro").html(response.bairro);
           $("#localidade").html(response.localidade);
           $("#uf").html(response.uf);
           $("#titulo_cep").html("CEP " + response.cep);
           $(".cep").show();
           $(".barra-progresso").hide();
           
         //document.getElementById("logradouro").innerHTML = response.logradouro;
           
          //alert(response.logradouro);
       }
   })
}

$(function(){
    $(".cep").hide();
    $(".barra-progresso").hide();
});
