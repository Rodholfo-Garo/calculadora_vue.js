# Montando uma calculadora com VUE.JS

- Primeiro Passo

  - Montar a Estutura HTML e estilizar com BootStrap

  - Recuperar os valores dos inputs e criar o estado para tarefa

    - ```javascript
      //Criar Estado
      const estado = reactive({
        operacao:'',
        numero1:'',
        numero2:'',
        resultado:'',
      });
      
      //Recuperar Valores dos inputs - v-model="estado.numero1" 
      <input v-model="estado.numero1" class="form-control" type="number" name="" id="numero1" placeholder="Insira o primeiro número">
      ```

  - Identificar operação selecionada no Select e Inserir o evento para identificar quando o select for alterado e executar a função que vai fazer a conta

    - ````javascript
       //v-model="estado.operacao" - Reponsavel por informar o valor de opção foi selecionada
      //@change="calculaResultado" - Quando houver alguma alteração no SELECT, este evento vai executar a função 'calculaResultado'
      <select v-model="estado.operacao" @change="calculaResultado" class="form-control fs-5 badge text-bg-primary">
              {{ estado.operacao}}
      
                <!-- atributos que controlam o comportamento do elemento. -->
                <option value="" disabled selected hidden>Operação</option>
                <option value="adicicao"> Soma +</option>
                <option value="subtracao">Subtração -</option>
                <option value="divisao">Divisão /</option>
                <option value="multiplicacao">Multiplicação *</option>
              </select>   
      ````

    - Criar a função para fazer a conta

      - ````javascript
        /*
        Quando inserir um numero no input numero1 e numero2, v-model vai capturar estes valores e armazenar no objeto estado.
        
        Quando selecionar a operação no select, o v-model="estado.operacao" vai armazenar o valor do option no objeto estado. E o evnto @change vai exectar a função calculaResultado, onde o switch vai receber a operação escolhida no select ( que esta armazenada em estado.operacao), procurar ela no loop, e executa-la
        
        */
        
        const calculaResultado = () => {
          switch(estado.operacao){
        
            case 'adicicao':
              estado.resultado = estado.numero1 + estado.numero2;
              break;
            case 'subtracao':
              estado.resultado = estado.numero1 - estado.numero2;
              break;
            case 'multiplicacao':
              estado.resultado = estado.numero1 * estado.numero2;
              break;
            case 'divisao':
              estado.resultado = estado.numero1 / estado.numero2;
              break;
              default:
              estado.resultado = 0;
          }
        }
        ````

      - 