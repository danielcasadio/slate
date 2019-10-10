# Errors

<aside class="notice">
This error section is stored in a separate file in <code>includes/_errors.md</code>. Slate allows you to optionally separate out your docs into many files...just save them to the <code>includes</code> folder and add them to the top of your <code>index.md</code>'s frontmatter. Files are included in the order listed.
</aside>

The Kittn API uses the following error codes:


Código do Erro | Significado
---------- | -------
400 | Requisição inválida
401 | Não autorizado -- Sua chave API está errada.
403 | Proibido -- A requisição só pode ser acessada por administradores.
404 | Não encontrado -- Requisição não encontrada
405 | Método não permitido -- Você tentou acessar um método inexistente.
406 | Inaceitável -- Sua requisição não está no formato JSON.
410 | Removido -- A requisição foi removida dos servidores.
418 | I'm a teapot.
429 | Too Many Requests -- You're requesting too many kittens! Slow down!
500 | Internal Server Error -- We had a problem with our server. Try again later.
503 | Service Unavailable -- We're temporarily offline for maintenance. Please try again later.
