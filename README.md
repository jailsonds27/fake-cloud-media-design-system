Desafio: FakeCloudMedia - System Design
Contexto do Problema
A FakeCloudMedia é uma empresa que oferece uma plataforma de gestão de conteúdo multimídia para seus clientes. A plataforma permite que usuários façam upload de arquivos (imagens e documentos), que são processados automaticamente e ficam disponíveis para consulta através de uma interface web moderna.

Funcionalidades Principais
Upload e Gerenciamento de Arquivos
Os usuários enviam arquivos através de uma aplicação web. O sistema deve fornecer feedback visual em tempo real sobre o status do envio, mostrando progresso da transferência, posição na fila de processamento e notificações de sucesso ou erro. Os arquivos são armazenados em um sistema de armazenamento em nuvem para garantir durabilidade e disponibilidade.

Processamento Assíncrono Inteligente
Quando um arquivo é enviado, o sistema aciona automaticamente um processo de validação e transformação. Uma função serverless publica uma mensagem em uma fila de processamento, que é consumida por containers escaláveis. Estes containers realizam validações de segurança, conversões de formato, extração de metadados e geração de thumbnails quando aplicável.

Persistência Híbrida de Dados
O sistema utiliza uma arquitetura de dados híbrida: informações estruturadas como metadados, dados de usuários e relações de negócio ficam em um banco relacional, enquanto logs de auditoria, histórico de processamento e dados analíticos ficam em um banco não relacional, otimizando performance e custos.

Exposição Segura da Aplicação
O backend é exposto através de um gateway de APIs que gerencia autenticação, autorização, rate limiting e versionamento. O frontend consome essas APIs para apresentar listas filtráveis de arquivos, detalhes de processamento e dashboards administrativos, tudo acessível através de um domínio personalizado.

Desafio
Como você estruturaria a arquitetura em nuvem dessa solução?
