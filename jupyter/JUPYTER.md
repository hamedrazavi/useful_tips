# Multi-cursor in jupyter
Jupyter notebook uses the [codemirror](https://www.codemirror.net/) (a text editor implemented in JavaScript for the browser) in the background. To edit or add shortcuts or features you need to update those of the codemirror. 

To do so, you need to update the custom.js of jupyter, normally located at ~/.jupyter/custom/custom.js. If this file or even the custom folder does not exist, make one. Then add the following contents to the custom.js:

~~~~
require(["codemirror/keymap/sublime", "notebook/js/cell", "base/js/namespace"],
    function(sublime_keymap, cell, IPython) {
        cell.Cell.options_default.cm_config.keyMap = 'sublime';
        cell.Cell.options_default.cm_config.extraKeys["Ctrl-Enter"] = function(cm) {}
        var cells = IPython.notebook.get_cells();
        for(var cl=0; cl< cells.length ; cl++){
            cells[cl].code_mirror.setOption('keyMap', 'sublime');
            cells[cl].code_mirror.setOption("extraKeys", {
                "Ctrl-Enter": function(cm) {}
            });
        }
    } 
);
~~~~

The source of this tip is Saravanabalagi, Ramachandran [here](https://stackoverflow.com/questions/41553806/atom-sublime-like-multiple-selections-in-jupyter).