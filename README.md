 const urlParams = new URLSearchParams(window.location.search);
    for (var [key, value] of urlParams) {
        if(document.getElementById(key)) {
            document.getElementById(key).innerText = `${value}`;
        } else if (window.debugMode) {
            document.write("unidentified keys <br/>");
            document.write(`${key} = ${value} <br/>`);
        } else {
            key = DOMPurify.sanitize(key);
            document.write(`<span style='color: red'>${key} not found in the document</span><br/>`);
        }
    }
