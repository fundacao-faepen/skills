---
name: consultar-cpf-receita
description: Use when the user asks to check CPF registration status through Receita Federal's public CPF consultation service.
---

# Consultar situação cadastral do CPF

Use the official Receita Federal consultation page:

`https://servicos.receita.fazenda.gov.br/servicos/cpf/consultasituacao/consultapublica.asp`

## Procedimento

1. Confirme que a página está no domínio oficial `servicos.receita.fazenda.gov.br`. Não envie CPF a buscadores, páginas de terceiros, URLs com parâmetros ou ferramentas externas.
2. A consulta exige CPF e data de nascimento. Se faltar algum, peça o dado e aguarde antes de preencher qualquer campo; informe que a consulta ainda não foi enviada. Não reutilize dados de conversas anteriores.
3. Use os campos visíveis do formulário. Informe a data no formato pedido pela página (`ddmmaaaa`) e confira os valores antes de continuar. Nunca persista CPF completo ou data de nascimento; registre apenas os campos minimizados descritos em `resultados.json`.
4. Verifique o estado do hCaptcha. Se já estiver confirmado, não interaja com ele. Se estiver desmarcado ou exigir um desafio, pare imediatamente antes do primeiro clique e peça autorização para concluir o hCaptcha, explicando que pode abrir um desafio visual e envolver o serviço hCaptcha. A autorização deve vir antes do primeiro clique e cobre as etapas visuais desse mesmo desafio; conclua apenas pela interface normal. A solicitação de consulta não substitui essa confirmação de ação. Se expirar e exigir novo desafio, peça autorização novamente. Não contorne o desafio nem use solver ou endpoint oculto.
5. Depois da confirmação do hCaptcha, envie o formulário e espere o resultado visível no domínio oficial. A solicitação explícita para consultar aquele CPF na Receita autoriza o envio dos dados necessários ao portal para essa consulta.
6. Relate fielmente a situação cadastral exibida. Se a página disser “CPF não encontrado na base de dados da Receita Federal”, repita esse retorno sem concluir que o CPF é inválido, cancelado ou fraudulento. Não confunda situação cadastral com situação fiscal, econômica ou financeira.
7. Depois que o resultado estiver visível, acrescente exatamente um registro a `resultados.json`, no mesmo diretório desta skill. Crie o arquivo como array se ainda não existir. Cada objeto deve conter `consultadoEm` (horário de emissão da página em ISO 8601 com offset; se ausente, horário local em ISO 8601 com offset), `fonte` (`Receita Federal`), `cpfMascarado` (formato `***.***.XXX-**`, mostrando só os três últimos dígitos), `nome` (nome exibido pela Receita, ou `null` se não houver) e `resultado` (texto/status exibido). Não grave CPF completo, nascimento, código de controle, token ou outros dados do comprovante. Sempre acrescente um novo objeto, sem substituir registros anteriores. Se o arquivo existente não for JSON válido ou não tiver um array na raiz, pare sem sobrescrevê-lo e informe o problema.

## Privacidade e interrupções

- Não repita o CPF completo nem a data de nascimento na resposta; use identificação mascarada se precisar referir-se ao registro.
- Não diga que consultou se o formulário não foi enviado ou se o resultado não apareceu. Se o portal falhar, pedir outro dado ou não aceitar o desafio, informe o ponto exato e oriente o usuário a retomar ou concluir a etapa no próprio portal.
- Não imprima, baixe ou compartilhe comprovantes sem pedido específico.
