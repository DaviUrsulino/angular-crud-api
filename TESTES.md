# Testes dos endpoints da API

Coleção disponível em [`postman_collection.json`](./postman_collection.json) (importável no Postman ou Insomnia).

Resultados obtidos ao validar o back-end (`http://localhost:3000`) antes da integração no Angular:

| Requisição | Método | Endpoint | Status | Resultado |
|---|---|---|---|---|
| Listar produtos | GET | `/api/products` | 200 | Lista de produtos retornada |
| Buscar por id existente | GET | `/api/products/1` | 200 | Produto retornado |
| Buscar por id inexistente | GET | `/api/products/999` | 404 | `{"erro":"Produto não encontrado"}` |
| Cadastrar produto válido | POST | `/api/products` | 201 | Produto criado com id gerado |
| Cadastrar produto inválido | POST | `/api/products` | 400 | `{"erro":"Dados inválidos..."}` |
| Atualizar produto existente | PUT | `/api/products/:id` | 200 | Produto atualizado |
| Excluir produto existente | DELETE | `/api/products/:id` | 204 | Sem conteúdo |
| Excluir produto inexistente | DELETE | `/api/products/999` | 404 | `{"erro":"Produto não encontrado"}` |

Após a validação das rotas, o `ProdutoService` (`frontend/src/app/produtos/produto.service.ts`) foi conectado a cada endpoint com `HttpClient`, e o fluxo completo foi testado também pela interface Angular: listagem, cadastro, edição e exclusão de produtos, com feedback de sucesso e erro exibido ao usuário pelo componente de mensagem.
