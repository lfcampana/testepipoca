# Introdução ao Kubernetes: Simplificando a Orquestração de Contêineres com Minikube, Argo CD e Metallb

O Kubernetes revolucionou a maneira como implantamos e gerenciamos aplicativos em contêineres. Neste artigo, vou guiá-lo em um passo a passo completo para criar um ambiente de desenvolvimento Kubernetes, desde a instalação do Minikube até a implantação de um aplicativo de exemplo utilizando o Argo CD e o Metallb.

Primeiro, você aprenderá como instalar o Minikube, uma ferramenta que permite executar um cluster Kubernetes em sua máquina local. Em seguida, vamos iniciar o cluster e criar um namespace dedicado para o Argo CD, uma ferramenta de Continuous Delivery que simplifica o processo de implantação de aplicativos no Kubernetes.

Além disso, vou explicar como habilitar o auto-complete do kubectl, tornando sua experiência com o Kubernetes ainda mais eficiente.

Após preparar o ambiente de desenvolvimento, vamos explirar a instalação do Metallb, uma solução de balanceamento de carga para clusters Kubernetes.

Por fim, para verificar se tudo está funcionando corretamente, faremos a implantação de um aplicativo de exemplo utilizando a imagem do Nginx.

Com este guia completo, você estará preparado para criar e gerenciar seu próprio ambiente de desenvolvimento Kubernetes, utilizando o Minikube, Argo CD e Metallb. Vamos começar instalando o Minikube e dando os primeiros passos rumo à orquestração de contêineres simplificada e eficiente, e de quebra com um terminal turbinado e com algumas features interessantes.! 

Enjoy.

# Sumário

- [Introdução ao Kubernetes: Simplificando a Orquestração de Contêineres com Minikube, Argo CD e Metallb](#introdução-ao-kubernetes-simplificando-a-orquestração-de-contêineres-com-minikube-argo-cd-e-metallb)
- [Sumário](#sumário)
  - [Preparando o ambiente](#preparando-o-ambiente)

---

## Preparando o ambiente

Vou considerar que para este artigo uma nova instalação do linux, logo se alguns dos itens abaixo para preparação ja estiverem sido feitos desconsidere o passo.

**Abra o terminal**
1. **Brew**:    
   ```shell 
    /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
   ```
   Após a instalação, no log de instalação irá exibir no terminal alguns comandos para incluir o Brew no PATH, execute os comandos e siga para o próximo passo 
2. **Tree**
    ```shell
    sudo apt-get install tree
    ``` 
3. **oh-my-posh**
    ```shell
    curl -s https://ohmyposh.dev/install.sh | bash -s    
    ```
    Feito o comando é necessario a instalação de uma fonte, no meu caso prefiro a fonte **"MesloLGM NF"**
    para realizar a instalação execute o comando `oh-my-posh font install`

    Após a instalação da fonte apenas para certificar execute o comando `oh-my-posh get shell` para validar se o seu terminal é o bash.

    Feito isso e confirmado que o terminal utilizado é o bash. Vamos Incluir o oh-my-posh para inciar com o terminal. Para fazer isso vamos fazer o seguinte: 
    ```shell
        vi ~/.bash_profile
        #inclua a linha abaixo no final do arquivo 
        eval "$(oh-my-posh init bash)"
    ```
    é possivel também utilizar temas customizados , vou deixar abaixo um link com um tema que criei para facilitar o uso para meu dia-dia. acredito que possa ajudar.
    para utilizar o tema substitua o a linha do init bash para a seguinte: 
    ```shell
        eval "$(oh-my-posh init bash --config tema)"
    ```
    
    substitua a palavra tema pelo [Meu tema](https://gist.github.com/lfcampana/34c0154d4d362bb1eb390a8b00272a84) ou procure por temas pela internet (existem milhares e são mto legais)

    
