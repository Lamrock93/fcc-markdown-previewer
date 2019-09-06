const renderer = new marked.Renderer(); // creates a Marked renderer...
renderer.link = function (href, title, text) {
  return `<a target="_blank" href="${href}">${text}` + '</a>';
} // calls the renderer and has it open in a new tab

marked.setOptions({ // performs line breaks for carridge returns
  breaks: true,
});

const INITIAL_TEXT = "# Cool Markdown Previewer\n## by Liam Washburn\nYou _may_ remember me from such programs as **Roman Numeral Converter**, and **Insightful Quote Generator**. Here is my [GitHub account](https://github.com/Lamrock93).\n\nHere is some code:\n\n```\n// this is multi-line code:\n\nfunction anotherExample(firstLine, lastLine) {\n\nif (firstLine == '```' && lastLine == '```') {\n    return multiLineCode;\n  }\n}\n```\n\n > Pee is stored in the balls - Winston Churchill\n\nHere is some code, `<div></div>`, between 2 backticks.\n\n![Shaq wearing a China hat!](https://thehype.files.wordpress.com/2006/08/shaqemperor1.jpg?w=425&zoom=2)\n\nBest NBA Players:\n 1. LeBron James\n 2. James Harden\n 3. Kawhi Leonard\n 4. ~Kevin Durant~ Stephen Curry\n 5. Giannis Antetokounmpo\n"

class MarkdownPreviewer extends React.Component {
  constructor(props) { // make a constructor with props
    super(props); // gotta gave a super!
    this.state = {
      userInput: INITIAL_TEXT // userInput is the only state that will change
    }
    this.handleChange = this.handleChange.bind(this); // gotta bind everything regarding state with this
  }
  
  handleChange(event) { // this is what allows the markdown previewer to be edited!
    this.setState({
      userInput: event.target.value
    })
    
  }
  render() { // rendering the html... The editor uses React to change the input in real time. The preview section interprets that input, using the MarkedJS libraries to display it in html. The syntax isn't as bad as it first appears
    return (
      <div id="wrapper">
    <textarea rows = "20" cols = "100" id="editor" onChange={this.handleChange}>{this.state.userInput}</textarea>
        <div> <span id='preview' dangerouslySetInnerHTML={{ __html: marked(this.state.userInput, { renderer: renderer }) }} /> </div>
        
      </div>
    )
  }
}

ReactDOM.render(<MarkdownPreviewer />, document.getElementById('app')); // always gotta render React stuff to the DOM!
