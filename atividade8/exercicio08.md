### Exercício 08: Tabela FIPE

Objetivo
Utilizando o framework Spring Web, implemente um controlador e um método que receba um objeto JSON no corpo da requisição contendo uma marca, modelo e ano de um carro e retorne o valor de tabela FIPE para esse carro. Utilize esta API como referência: https://deividfortuna.github.io/fipe/

Instruções

Crie um novo projeto Spring Boot usando o Spring Initializr.
Defina uma classe de controlador com a anotação @RestController.
Crie um método que receba um objeto JSON no corpo da requisição contendo uma marca, modelo e ano de um carro e retorne o valor de tabela FIPE para esse carro.
Use o RestClient para fazer a requisição à API da Tabela FIPE.


### Entradas (inputs)

{
  "marca": "Fiat",
  "modelo": "Uno",
  "ano": 2023
}



Saídas (outputs)

{
  "valor": 50000.0
  "mes": "Setembro de 2024"
}


## RESOLUÇÃO ##

public class CarroRequest {
    private String marca;
    private String modelo;
    private Integer ano;

    
}

 public class CarroResponse {
    private String valor;
    private String mes;

    
}
   
@RestController
@RequestMapping("/fipe")
public class FipeController {

    @Autowired
    private FipeService fipeService;

    @PostMapping("/valor")
    public ResponseEntity<CarroResponse> obterValorFipe(@RequestBody CarroRequest carroRequest) {
        CarroResponse response = fipeService.obterValorFipe(carroRequest);
        return ResponseEntity.ok(response);
    }
}

@Service
public class FipeService {

    private static final String URL_BASE = "https://parallelum.com.br/fipe/api/v1";

    public CarroResponse obterValorFipe(CarroRequest carroRequest) {
        String url = String.format("%s/%s/%s/%s/%d", URL_BASE, carroRequest.getMarca(), carroRequest.getModelo(), carroRequest.getAno());
        
        RestTemplate restTemplate = new RestTemplate();
        ResponseEntity<Map> response = restTemplate.getForEntity(url, Map.class);

        String valor = (String) response.getBody().get("Valor");
        String mesReferencia = (String) response.getBody().get("MesReferencia");

        CarroResponse carroResponse = new CarroResponse();
        carroResponse.setValor(valor);
        carroResponse.setMes(mesReferencia);

        return carroResponse;
    }
}

@Configuration
public class AppConfig {

    @Bean
    public RestTemplate restTemplate() {
        return new RestTemplate();
    }
}
