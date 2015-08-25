acorn-to-esprima

Some functions to help transform an acorn/babel ast to esprima format.

Primarily for use in [babel-eslint](https://github.com/babel/babel-eslint), [babel-jscs](https://github.com/jscs-dev/babel-jscs), and [ast explorer](https://github.com/fkling/esprima_ast_explorer)

There are no dependencies (the methods are changed to pass dependencies in when used)

The current functions exposed are:

// method to fix issues between comments in the ast
- function attachComments(ast, comments, tokens)
  - This modifies the comments passed in.
// converts tokens from acorn to esprima
- function toTokens(tokens, tt)
  - tt is `require("babel-core").acorn.tokTypes`
  - Converts template string tokens (`convertTemplateType`)
  - filters out comment tokens
  - runs toToken over each token
- function toToken(token, tt)
  - Sets token.type, token.range, and token.value
- function toAST(ast, traverse)
  - traverse is `require("babel-core").traverse;`
  - traverses over the ast and makes any necessary changes (usually es6+)
- function convertComments(comments)
  - Modifies comment.type