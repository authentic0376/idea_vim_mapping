# idea_vim_textobj-line-like_mapping

To map `il` for "inner line" similar to `viw`, `diw`, and `ciw` for "inner word", add the following to the end of your `.ideavimrc` file:


```
xnoremap il ^o$
nnoremap dil v^o$d
nnoremap yil v^o$y
nnoremap cil v^o$c
```

In Vim, the default yy copies the entire line, including the leading and trailing whitespace.
The il mapping, however, represents the line excluding the surrounding whitespace.

## Limitation in IdeaVim

In visual mode, `il` can be handled easily. On the other hand, mappings like `dil`, `yil`, and `cil` fall under operator-pending mode. In operator-pending mode, an atomic cursor movement must follow the operator. Consider examples like `diw`, `dw`, or `d$`. These represent single, atomic movements based on the current cursor position. However, selecting a line excluding leading and trailing whitespace cannot be achieved with such atomic movements. 

To achieve this, you would need to use functions or keywords like `normal` or `call`. Unfortunately, IdeaVim does not support these features. As a result, you cannot map `il` using `onoremap il ...`. While inefficient, each mapping must be created individually in normal mode.

## Additional Mappings

You can create more mappings like `g~il` as needed for other operations.