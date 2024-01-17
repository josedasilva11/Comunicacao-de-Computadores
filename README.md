# Módulo Transporte

##  Transferência Confiável de Dados

***Princípio:*** 

Garantir que todos os dados enviados cheguem ao destinatário sem erros e na ordem correta.

***Técnicas:***

- ***Retransmissão:***
 Se não houver confirmação de recebimento (ACK) dentro de um tempo esperado, os dados são retransmitidos.
- ***Confirmações (ACKs) e Temporizadores:***
 O receptor envia ACKs para confirmar a recepção de pacotes. Temporizadores são usados para detectar perdas de pacotes.
- ***Controle de Erros:***
 Além das retransmissões, usa-se verificação de erros como checksum para garantir a integridade dos dados.

##  Controlo de Fluxo

 ***Objetivo:***
 
 Evitar que o emissor sobrecarregue o receptor com dados.
 
***Mecanismo de Janela Deslizante:*** 

O receptor especifica a quantidade de dados que está pronto para receber (janela de recepção). O emissor pode enviar apenas a quantidade de dados indicada pela janela.


##  Controlo de Congestão


***Desafio:***

Evitar sobrecarga na rede que pode levar a atrasos e perdas de pacotes.
***Mecanismos:***


- ***Slow Start:***
   Inicia com uma janela de congestão pequena e a aumenta exponencialmente até detectar perda de pacotes.
- ***AIMD:***
   Após a detecção de perda, reduz a janela de congestão multiplicativamente e depois aumenta aditivamente durante a fase de evitação de congestão.
- ***Fast Retransmit e Fast Recovery:***
   Permite uma rápida recuperação após a detecção de perda de pacotes.

##  UDP (User Datagram Protocol)

***Características:***

- ***Sem Conexão:*** Não estabelece uma conexão antes de enviar dados.
- ***Sem Controle de Erro:*** Não há retransmissões ou confirmações.
- ***Baixo Overhead:*** Ideal para aplicações que requerem transmissão rápida.

##  TCP (Transmission Control Protocol)

***Funcionalidades:***

- ***Estabelecimento de Conexão:*** Utiliza o processo de 3-way handshake.
- ***Transferência de Dados Ordenada e Fiável:*** Usa números de sequência para garantir a ordem e a integridade.
- ***Controlo de Fluxo e Congestão:*** Usa janelas de recepção e algoritmos de controle de congestão.

##  Multiplexagem e Desmultiplexagem

***Função:***

Permitir que múltiplas conexões TCP ou UDP ocorram simultaneamente entre diferentes aplicações em um host, usando números de porta para direcionar o tráfego.

##  Estabelecimento e Término de Conexões TCP

- ***3-way Handshake:*** Inicia a conexão sincronizando e reconhecendo os números de sequência.
- ***Encerramento de Conexão:*** Utiliza um processo de 4 passos com mensagens FIN e ACK para terminar a conexão de maneira limpa.

##  Controle de Erros e Retransmissão no TCP

***Mecanismos:***

Quando um pacote é perdido (detectado por timeout ou ACKs duplicados), o TCP retransmite o pacote. Usa checksums para a detecção de erros nos dados.

##  Operações Específicas do TCP

- ***Controle de Fluxo:*** Ajusta dinamicamente o tamanho da janela de recepção com base na capacidade do receptor.
- ***Controle de Congestão:*** Adapta o tamanho da janela de transmissão com base na percepção da congestão da rede, evitando assim a perda de pacotes.

# Módulo HTTP (Hypertext Transfer Protocol)


## Conceitos Básicos

- ***Páginas Web:*** Consistem em objetos dentro de um ficheiro base HTML, que podem incluir referências a outros objetos ou páginas.
- ***Objetos:*** Incluem ficheiros HTML, imagens JPEG, applets Java, ficheiros áudio, etc.
- ***URLs:*** Cada objeto é identificado por um Uniform Resource Locator.

## Funcionamento do HTTP

- ***Protocolo de Nível de Aplicação:*** Modelo cliente/servidor onde o cliente (browser) solicita e recebe objetos Web, e o servidor envia objetos em resposta.
- ***Versões do HTTP:*** Variações incluem HTTP 0.9, 1.0, 1.1, 2, e 3.
- ***Estado:*** Protocolo sem estado, não mantendo informação sobre pedidos anteriores.

## Mensagens HTTP

- ***Pedido HTTP:*** Inclui uma linha de pedido, linhas de cabeçalho e, ocasionalmente, um corpo.
- ***Resposta HTTP:*** Semelhante ao pedido, com uma linha de status e cabeçalhos.
- ***Métodos HTTP:*** GET, POST, HEAD, PUT, DELETE, etc., cada um com propósitos específicos (ex: GET para solicitar recursos, POST para enviar dados).

## HTTP e TCP

- ***Uso do TCP:*** HTTP utiliza TCP para conexão (padrão na porta 80).
- ***HTTP Não Persistente vs. Persistente:*** Varia entre uma única transação por conexão (HTTP/1.0) e múltiplas transações (HTTP/1.1 e superior).

## HTTP/2 e HTTP/3

- ***Melhorias no Desempenho:*** HTTP/2 introduz multiplexação, compressão de cabeçalho e push do servidor.
- ***QUIC e HTTP/3:*** Transição de alguns elementos para QUIC (baseado em UDP) para melhorar o desempenho e a segurança.

## Cookies e Estado

- ***Cookies:*** Mecanismo para manter estado e informações entre as transações HTTP.

## Proxy e Cache

- ***Servidores Proxy:*** Usados para cache e otimização de requisições e respostas HTTP.
- ***Melhoria de Desempenho:*** Reduzem tempo de resposta e tráfego na rede.

# Módulo DNS

## Conceitos Fundamentais do DNS

- ***Função:*** Traduzir nomes de domínio legíveis por humanos (como www.google.com) em endereços IP.
- ***Características:*** É uma base de dados distribuída e hierárquica, com um protocolo de camada de aplicação.
  
## Por que não Centralizar o DNS?

- Problemas de centralização incluem ponto único de falha, volume de tráfego elevado, distância da base de dados centralizada e dificuldades de manutenção.
  
## Serviços DNS

- Tradução de nomes de hosts para endereços IP.
- Aliases de hosts e definição de servidores de e-mail.
- Distribuição de carga entre servidores Web replicados.
  
## Hierarquia do DNS

- ***Servidores Root DNS:*** Pontos de partida para as consultas DNS.
- ***TLD (Top-Level Domain) Servers:*** Responsáveis por domínios de topo (.com, .org, .pt, etc.).
- ***Servidores DNS Autoritativos:*** Mantêm informação precisa sobre domínios específicos.
  
## Operação do DNS

- ***Modos Iterativo e Recursivo:*** Diferentes métodos para resolver nomes.
- Uso do UDP para eficiência.
- Caching para reduzir a carga nos servidores.
  
## Segurança no DNS

- Vulnerabilidades incluem ataques DDoS, redirecionamentos e DNS poisoning.
- Mecanismos de segurança como DNSSEC para aumentar a confiabilidade.
  
## Ferramentas de Cliente DNS

- Utilitários como host, nslookup e dig para consultas diretas ao DNS.
  
## Recordes de Recursos DNS

- Diversos tipos como A, NS, CNAME, MX, SOA, etc.
- Armazenam informações específicas sobre domínios e seus serviços associados.
  
## Implementação e Gestão de Domínios

- Processos para configurar e gerir domínios e seus respectivos servidores DNS.
- Exemplos de configurações de domínio e registros DNS.
  
## Programação e Integração com DNS

- Utilização de APIs e bibliotecas em linguagens de programação como Java e C para realizar consultas DNS.


# Módulo Segurança de Redes

## Tipos de Ataques

- ***Espionagem:*** Interceção indevida de mensagens
- ***Inserção de Mensagens:*** Comunicação fraudulenta
- ***Disfarce (Spoofing):*** Fingir ser outro usuário
- ***Desvio de Sessões (Hijacking):*** Tomar controle de conexões ativas
- ***Negação de Serviço (DoS):*** Impedir acesso legítimo a serviços

## Propriedades de Comunicação Segura

- ***Confidencialidade:*** Mensagens compreensíveis apenas pelo emissor/receptor
- ***Autenticação:*** Confirmação mútua de identidades
- ***Integridade da Mensagem:*** Mensagem não alterada durante a transmissão
- ***Não Repúdio:*** Impedir negação de participação em comunicação
- ***Acesso e Disponibilidade:*** Serviços acessíveis e operacionais para usuários autorizados


## Criptografia

- ***Chave Simétrica:*** Mesma chave para cifragem e decifragem
- ***Chave Pública:*** Chave para cifrar é pública, para decifrar é privada
- ***Chave Simétrica:*** Inclui cifra de substituição e criptografia de bloco (DES, 3-DES, AES)
- ***Ataques a Chave Simétrica:*** Baseados em texto cifrado, texto conhecido e texto escolhido

## Criptografia de Chave Pública

- ***RSA:*** Algoritmo popular com propriedade
  
![Equação](https://latex.codecogs.com/png.image?\inline&space;\dpi{110}\bg{black}&space;K_B(K_B^{-1}(m))=m)

- ***Autenticação e Confidencialidade::*** Uso das chaves pública e privada
- ***Assinatura Digital::*** Associação do assinante ao documento, garantindo integridade e não repúdio

## Infraestrutura de Chaves Públicas (PKI)

- ***Autoridade de Certificação (CA)::*** Associa chave pública a uma entidade
- ***Certificado Digital::*** Vincula chave pública a uma identidade verificável

## TLS (Transport Layer Security)

- ***Evolução do SSL:*** Protocolo para segurança em comunicações de rede
- ***TLS 1.3 (2020):*** Melhorias na segurança e desempenho, redução do handshake
- ***Aplicação:*** Utilizado em diversas aplicações sobre TCP para autenticação, confidencialidade e integridade


# Módulo Encaminhamento

## Conceitos Fundamentais

- ***Forwarding:*** Processo de mover pacotes de uma entrada para a saída apropriada em um roteador.
- ***Routing:*** Determinação de rotas para o encaminhamento dos pacotes pela rede.

## Algoritmos de Encaminhamento Dinâmico

- ***Estado de Ligação (Link State - LS):*** Todos os roteadores têm conhecimento completo da topologia e custos de ligação.
- ***Vetores de Distância (Distance Vector - DV):*** Roteadores conhecem apenas vizinhos diretos e custos associados.
- ***Comparação entre DV e LS:*** LS é mais robusto e rápido na convergência, mas mais exigente em recursos; DV é mais simples, mas tem problemas de convergência lenta e loops.

## Protocolos de Encaminhamento IP

- ***Protocolos Internos (IGP):*** Usados dentro de um Sistema Autónomo (AS), como RIP, OSPF, EIGRP.
- ***Protocolos Externos (EGP):*** Usados para encaminhamento entre diferentes AS, principalmente BGP.

## Encaminhamento IP em Detalhe

- ***Roteadores e Interfaces:*** Roteadores armazenam e reenviam datagramas IP, tratando diferentes tipos de interfaces de rede.
- ***Tabelas de Encaminhamento:*** Usadas para determinar o próximo salto e interface de saída para cada destino.
- ***Plano de Controlo e Plano de Dados:*** Separação entre a lógica de encaminhamento (controlo) e a movimentação de dados (dados).

## Algoritmos de Encaminhamento

- ***Link State (LS):*** Utiliza o algoritmo de Dijkstra para calcular rotas de custo mínimo. Exige conhecimento global da rede.
- ***Distance Vector (DV):*** Utiliza o algoritmo de Bellman-Ford. Baseia-se em informação local e é iterativo e assíncrono.

## Problemas e Soluções nos Algoritmos DV

- ***Problemas:*** Convergência lenta e possibilidade de loops.
- ***Soluções:*** Divisão do horizonte e envenenamento do percurso inverso para evitar loops.

## Encaminhamento na Internet

- ***Sistemas Autónomos (AS):*** Agrupamento de roteadores sob a mesma administração.
- ***IGP vs EGP:*** IGP foca no desempenho interno, enquanto EGP lida com políticas e relações entre diferentes AS.
