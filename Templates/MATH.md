<%*
function c(order){
	// Add cursor
	return "\<\% tp.file.cursor("+order+") \%\>";
}
let list = {
	// For latex suite
	"ls":"\{trigger: \""+c(1)+"\", replacement: \""+c(2)+"\", options: \""+c(3)+"\"\},",
	// For math
	"c": c(1),// add cursor
	"$4": " \$"+c(1)+"\$ "+c(2),
	"\\be": "\\begin\{"+c(1)+"\}\n"+c(2)+"\n\\end\{"+c(3)+"\}",
	"\_\-\{\}": "\_\{\}",
	"\^6\{\}": "\^\{\}",
	"\/frac": "\\frac\{"+c(1)+"\}\{"+c(2)+"\}"+c(3),
	"bf mathbf": "\\mathbf\{\}",
	"bb mathbb": "\\mathbb\{\}",
	"alpha": "\\alpha",
	"beta": "\\beta",
	"gamma": "\\gamma",
	"psi": "\\psi",
	"x chi": "\\chi",
	"epsilon": "\\epsilon",
	"sigma": "\\sigma",
	"tau": "\\tau",
	"ro rho": "\\rho",
	"mu": "\\mu",
	"delta": "\\delta",
	"l": "\\left",
	"r": "\\right",
	"+-": "\\pm",
	"l\<\,": "\\left\<",
	"l\|\\": "\\left\|",
	"r\>\.": "\\right\>",
	"r\|\\": "\\right\|",
	"l\{\[r\}\]": "\\left\\\{"+c(1)+"\\right\\\}"+c(2),
	"\|\\\>\.": "\\left\|"+c(1)+"\\right\>"+c(2),
	"\<\,\|\\": "\\left\<"+c(1)+"\\right\|"+c(2),//真的会有人单独写左矢吗？
	"\<\,\>\.": "\\left\<"+c(1)+"\\right\>"+c(2),
	"\<\,\|\\\>\.": "\\left\<"+c(1)+"\|"+c(2)+"\\right\>"+c(3),
	"\|\\\\psi\>\.": "\\left\|\\psi\\right\>",
};
let keys = Object.keys(list);
let key = await tp.system.suggester(keys, keys);
let value = list[key];
return value;
%>