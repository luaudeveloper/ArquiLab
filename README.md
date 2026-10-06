# 🖥️ Laboratório Virtual de Arquitetura de Computadores

Laboratório virtual para experimentação e comparação de diferentes configurações de arquiteturas de computadores, utilizando o **Logisim-Evolution** como motor de simulação e uma **interface web** como camada de interação.

A proposta é permitir que estudantes executem pequenos programas, acompanhem o funcionamento interno da arquitetura em tempo real e analisem métricas de desempenho sem precisar instalar ou manipular diretamente o Logisim.

> **Configura → Executa → Mede → Compara → Entende**

---

## 🎯 Sobre o projeto

Este projeto está sendo desenvolvido como um **Projeto Integrador (PI) de graduação** na área de Arquitetura de Computadores.

A ideia surgiu da necessidade de proporcionar uma experiência mais prática e visual para o estudo de conceitos como:

- CPU;
- ULA;
- registradores;
- memória;
- cache;
- ciclos de clock;
- execução de instruções;
- pipeline;
- desempenho de diferentes arquiteturas.

Em vez de recriar o funcionamento do Logisim no navegador, o projeto utiliza o **Logisim-Evolution como simulador real**, enquanto a aplicação web fornece uma interface simplificada para controlar e acompanhar a execução.

---

## ❓ Pergunta norteadora

> **Como a experimentação virtual de diferentes configurações de uma arquitetura de computadores pode contribuir para a compreensão de seu funcionamento e desempenho?**

---

## 🎯 Objetivo

Desenvolver um laboratório virtual que permita experimentar e comparar diferentes configurações de uma arquitetura de computadores através de uma interface web.

### Objetivos específicos

- Simular CPU, ULA, registradores, memória e cache;
- Executar pequenos programas;
- Permitir a visualização do funcionamento da arquitetura;
- Coletar métricas de desempenho;
- Comparar diferentes configurações;
- Facilitar a experimentação por parte dos estudantes;
- Disponibilizar o laboratório através de um navegador.

---

# 🏗️ Arquitetura

A aplicação será composta por diferentes camadas:

```text
┌─────────────────────────────────────────────┐
│                  NAVEGADOR                  │
│                                             │
│              Next.js / React                │
│                                             │
│  ┌──────────┐ ┌──────────┐ ┌────────────┐ │
│  │ Controle │ │ Métricas │ │ Comparação │ │
│  └──────────┘ └──────────┘ └────────────┘ │
│                                             │
│             Logisim ao vivo                 │
└─────────────────────┬───────────────────────┘
                      │
               HTTP / WebSocket
                      │
┌─────────────────────▼───────────────────────┐
│                  BACKEND                    │
│                                             │
│              Node.js / TypeScript           │
│                                             │
│  • Gerenciamento de sessões                │
│  • Controle do simulador                   │
│  • Comunicação em tempo real               │
│  • Coleta de métricas                      │
└─────────────────────┬───────────────────────┘
                      │
                 Controller
                      │
┌─────────────────────▼───────────────────────┐
│             LOGISIM-EVOLUTION               │
│                                             │
│                    Java                     │
│                                             │
│     CPU • ULA • RAM • Cache • Registros    │
└─────────────────────┬───────────────────────┘
                      │
                 Captura da tela
                      │
┌─────────────────────▼───────────────────────┐
│                STREAMING                    │
│                  VNC/noVNC                  │
└─────────────────────┬───────────────────────┘
                      │
                      ▼
                  NAVEGADOR
