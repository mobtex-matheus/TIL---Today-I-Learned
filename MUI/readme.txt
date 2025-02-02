

MATERIAL-UI

Biblioteca de design system, assim como Chakra-ui, essa biblioteca vem com componetnes pre-prontos
podendo você estilizar shapes e cores.

Para o uso desses componentes pre-prontos basta uma importação dentro do componente sendo criado.

----------------------------------------------------------------------

Material-ui com React

Para instalarmos o React digitamos no terminal:

yarn create react-app *nome do seu programa*

Após a criação adicionamos o MUI

yarn add @material-ui/core.

----------------------

Importações

Na documentação mostra como podemos fazer a importação de um unico componente por sua lib:

import Button from '@material-ui/core/Button' 

Mas podemos usar uma única importação para quase todos componentes:

import Button from '@material-ui/core/Button' 

----------------------

Utilização

Assim como um componente chamamos o componente do MUI usamos a semantica seguinte:

import Button from '@material-ui/core/Button'

function App() {
  return (
      <Button>
        Hello World
      </Button> <- Componente MUI     !!!!
    <div className="App">
      <header className="App-header">
        <img src={logo} className="App-logo" alt="logo" />
      </header>
    </div>
  );
}

----------------------

Estilização

Como estamos lidando com um design system a estilização de seus componentes é feita in-line.

Passamos o "modelo" do botão com a propiedade (variant)

import Button from '@material-ui/core/Button'

function App() {
  return (
    <Button variant="text">Text</Button> <- Botão sem preenchimento
    <Button variant="contained">Contained</Button>
    <Button variant="outlined">Outlined</Button> 
    <div className="App">
      <header className="App-header">
        <img src={logo} className="App-logo" alt="logo" />
      </header>
    </div>
  );
}


Para darmos cor aos nossos componentes passamos a prop (color)

<Button color="primary">Contained</Button>


Como todo botão, os botões do MUI também podem receber (href) para linkarmos

<Button href="*link*">Contained</Button>

Esses componentes do MUI também podem receber eventos Javascript assim como um HTML button

<Button onClick={() => alert("hello World")}>Contained</Button>

Podemos também passa a propiedade para desabilitar o button

<Button disabled>Contained</Button>

Alteramos o tamanho do componente com a prop (size)

<Button size="large">Contained</Button>
<Button size="medium">Contained</Button>
<Button size="small>Contained</Button>

Para sobre escrever estilizações padrões do Material-Ui usamos a props (styles)
Exemplo: Caso a cor padrão de um botão venha azul podemos sobre escreve-lo assim:

<Button styles={color="primary.red"}>Contained</Button>

----------------------------------------------------------------------

Uso de Icones com MUI

Antes de tudo é necéssario instalarmos a biblioteca de icons do MUI

yarn add @material-ui/icons

*Caso seu servidos (localhost) estiver rodando é necéssario reiniciar o mesmo

----------------------

Importações dos Icones

Para usarmos os icones baixados, fazemos a importação de um componente, ou seja, sem chaves

import SaveIcon from '@material-ui/icons/SaveIcon'
import { Save, ThreeDRotation } from "@material-ui/icons";

----------------------

Uso dos Icones

Como dito, esse icones são importados como componentes e o uso também será como componente

Dentro de um Button passamos o icone como prop, mas ainda sim o icone é referenciado com um componente

Podemos adicionar um Icone no inicio do button com:

<Button startIcon={<Save/>}>Contained</Button>

E ao final do Button com:

<Button endIcon={<Save/>}>Contained</Button>

----------------------

Button Group 

O button group é um componente e funciona pra mesclar os botões dentro dele, dando um visual mais atrativo.

Ele transforma dois botões em um único botão e no seu início e fim com bordar arredondas.

----------------------

Importação ButtonGroup 

O Button group vem por padrão dentro no @material-ui/core
Para sua importação utilizamos a seguinte linha:

import ButtonGroup from '@material-ui/core/ButtonGroup'

----------------------

Exemplo:

import ButtonGroup from '@material-ui/core/ButtonGroup'

export function ButtonGroup() {
    return(
        <ButtonGroup>
            <Button>
              First Button  
            </Button>
            <Button>
              Second Button  
            </Button>
        </ButtonGroup>
    )
}

Isso deve retornar dois botões mesclados.

----------------------

Estilos do Button Groups

Podemos dar estilizações todos butões dentro do Button Group inserindo propiedades ao componente:

import ButtonGroup from '@material-ui/core/ButtonGroup'

export function ButtonGroup() {
    return(
        <ButtonGroup variant="contained">
            <Button>
              First Button  
            </Button>
            <Button>
              Second Button  
            </Button>
        </ButtonGroup>
    )
}

----------------------------------------------------------------------

CheckBox

Checkbox são utilizados dentro de formularios

O componente checkbox no MUI se faz necéssario o uso da lógica de desestruturação
 e é viável cria-lo em um componente separado.

Exemplo:

export function ExemploCheckBox(){
  const {checked, setChecked} = React.useState(true)

  return(
    <Checkbox/>
  )
}

----------------------

Propiedades obrigatorias do checkbox

O componente CheckBox do MUI recebe por padrão propiedades para que funcione, 
caso contrário ele não funcionará, as propiedades:

export function ExemploCheckBox(){
  const [checked, setChecked] = React.useState(true)

  return(
    <Checkbox
    checked={checked}     <- verificação se está true or false
    onChange={(e) => {setCheked(e.target.checked)}} <- Mudança de estado 
    />
  )
}

----------------------

Propiedades

Como os outros componentes o check box recebe outras propiedades de estilização:

export function ExemploCheckBox(){
  const [checked, setChecked] = React.useState(true)

  return(
    <Checkbox
    color="primary"
    disabled
    />
  )
}

----------------------------------------------------------------------

Forms em MUI

MuiFormControlLabel

Instalando depêndencias:

yarn add @emotion/react
yarn add @emotion/styled

Como importar:

import FormControlLabel from '@mui/material/FormControlLabel';
 ou
import { FormControlLabel } from '@mui/material';

----------------------

Como utilizar?

O FormControlLabel irá funcionar como um container par unirmos label's com outro elemento

<FormControlLabel
  control={
    <Checkbox 
    inputProps={{
      'aria-label': 'secondary checkbox'
    }}
    />}
  label="Label do checkbox"
/>

----------------------

Propiedades

-> control
Elemento de controle para instanciar Radio, Switch ou Checkbox.

-> label
Como no HTML normal, usado para nomear tags

Você pode achar todas propiedades em: https://mui.com/pt/api/form-control-label/#main-content

----------------------------------------------------------------------

MakeStyles

O makestyles é utilizado para nós criarmos nossa propia personalizada

Como importar?:

import {makeStyles} from "@material-ui/core/styles"

----------------------

Modo de uso:

Como dito anteriormente usamos o makeStyles para personalizar todos os componentes da nossa maneira, para isso criamos
uma const fora da função ou um arquivo especial para estilizações, por exemplo podemos personalizar o nosso root:

!Exemplo com a const dentro do própio arquivo!

import {makeStyles} from "@material-ui/core/styles"

const useStyles = makeStyles({
  root:{
    estilizações...
  }
})

function ButtonStyled(){
  const classes = useStyles();

  return <Button className={classes.root}>Teste</Button>
}

Dessa forma passamos somente as estilizações de root ou qual seja a classe de forma singular ao componente.

----------------------

ThemeProvider

O theme provider é utilizado para criarmos variaveis de estilização como cores, shapes de um componente e tipografias.
Usado em volta da aplicação para que todos os lugares da aplicação tenham acesso as estilizações.

Como importar?:

import {ThemeProvider} from "@material-ui/core/styles"

Como dito anteriormente usamos o Theme Provider na camada App.js ou na camada index.js.

----------------------

Cores no Theme Provider

Para criamos nossa variaveis de cores podemos criar um arquivo a parte para exportarmos um theme e passa 
como prop pro ThemeProvider.

Como criar?

1° - importação

import { createTheme } from "@mui/material/styles";

2° criação de uma constante 

const theme(theme é definido por boas práticas) = createTheme ({
  palette: {
    primary: {
      main: "#010101",
    },
    secondary: {
      main: "#FFFFFF",
    },
  },
})

!para mais opções de cores dentro da "class" primary existem palavras reservadas para setarmos as variaveis

const theme = createTheme({
  palette: {
    primary: {
      main: '#0971f1',
      darker: '#053e85',
    },
    neutral: {
      main: '#64748B',
      contrastText: '#fff',
    },
  },
});

----------------------

Tipografia

A tipografia se faz útil quando temos que estilzar nossa fonte

Para o uso de uma fonte externa temos dois modos para usa-la:

1° importando:

<link
      href="https://fonts.googleapis.com/css2?family=Poppins:wght@700&family=Roboto:wght@400;500&display=swap"
      rel="stylesheet"
    />

2° Instalando:

yarn add fontsource-roboto(ou fonte desejada)

!Instalando você precisará importar a fonte onde ela for chamada:

import 'fontsource-roboto(fonte desejada)';



Podendo também ser usado como componente importamos o Typography como componente:

import Typography from '@mui/material/Typography';

Modo de uso

Podemos uso o Typography para criarmos títulos como h1 e etc:


<Typography variant="h1"></Typography>


*lista de variant existentes: https://mui.com/pt/components/typography/#component
Podemos brincar com esse componente:


<Typography variant="h1" component="div"></Typography>


Esse componente será uma div que recebe a estilizaçãode um h1


Typography no theme


Podemos estilizar as variantes dentro de Typography:
Basta criarmos um objeto typography dentro da const theme...


const theme = createTheme({

  typography:{
    h2: {
      fontSize: 36,
    }
  },
  palette: {
    primary: {
      main: '#0971f1',
      darker: '#053e85',
    },
    neutral: {
      main: '#64748B',
      contrastText: '#fff',
    },
  },
});

----------------------------------------------------------------------

Container / Grid 
No MUI Container e Grid são componentes
Sendo assim, importamos ambos para o uso.


import Container from '@material-ui/core/Container'


Por padrão o Container vem com maxWidth
Podemos alterar o tamanho usando maxWidth no componente.
O maxWidth recebe valores como sm - small, md - medium, lg -large e xs - extra large.


Grid
O meio de importar continua igual pro componente


import Grid from '@material-ui/core/Grid'


Existem dois tipos de Grid:

Container:
Esse fica em volta dos itens á serem organizados:


<Grid container></Grid>


Ainda dentro de container, escolhemos o espaçamento usando spacing


<Grid container spacing={numero a escolha}></Grid>


E podemos alinhar o conteúdo utilizando justify


<Grid container justify="center"></Grid>


Item:
Esse será o container de cada item a ser organizado


<Grid item></Grid>
----------------------------------------------------------------------

Paper

O fundo de uma aplicação se assemelha a textura lisa e opaca de uma folha de papel e o comportamento de uma aplicação imita a habilidade do papel de ser redimensionado, embaralhado e amontoado em várias folhas.

O componente Paper é uma div pre estilizada que pode receber variant e outras props:

<Paper elevation={0} /> (aplica shadow ao redor)
<Paper />
<Paper elevation={3} />

<Paper variant="outlined" /> (borda redonda)
<Paper variant="outlined" square /> (borda quadrada)

----------------------------------------------------------------------

Breakpoints

Para aprendermos responsividade no MUI precisamos primeiramente decorar o tamanho das telas:

xs = mobile;
sm = mobile;
md = tablet;
lg = desktop;

Com isso, aplicamos dentro dos containers e grids para definir tamanhos nos diferentes tipos de tela

----------------------------------------------------------------------

AppBar
Componente utilizado para criarmos nosso header

Esse componente pode receber outros componentes dentro dele e também receber props de esilização.
Por padrão ele criar um Container no header da aplicação e dentro dele você inseri os componentes que precisa.

----------------------------------------------------------------------

Escoped styles

const useStyles = makeStyles({
  btn: {
    fontSize: 60,
    backgroundColor: 'violet',
    '&:hover': {
      background: 'blue'
    },
  },
  title: {
    textDecoration: 'underline',
    marginBottom: 20,
  }
})

export default function Create() {
  const classes = useStyles()

  return (
    <Container size="sm">
      <Typography
        className={classes.title}
        variant="h6" 
        color="textSecondary"
        component="h2"
        gutterBottom
      >
        Create a New Note
      </Typography>

      <Button
        className={classes.btn}
        onClick={() => console.log('you clicked me')}
        type="submit" 
        color="secondary" 
        variant="contained"
        endIcon={<KeyboardArrowRightIcon />}>
        Submit
      </Button>

      
    </Container>
  )
}

----------------------------------------------------------------------

Input Adornment

Importação

import { InputAdornment } from '@mui/material';

----------------------

TextField

<TextField id="outlined-basic" label="Outlined" variant="outlined" />
<TextField id="filled-basic" label="Filled" variant="filled" />
<TextField id="standard-basic" label="Standard" variant="standard" />

----------------------

Validação

 <Box
      component="form"
      sx={{
        '& .MuiTextField-root': { m: 1, width: '25ch' },
      }}
      noValidate
      autoComplete="off"
    >
      <div>
        <TextField
          error
          id="outlined-error"
          label="Error"
          defaultValue="Hello World"
        />
        <TextField
          error
          id="outlined-error-helper-text"
          label="Error"
          defaultValue="Hello World"
          helperText="Incorrect entry."
        />
      </div>
      <div>
        <TextField
          error
          id="filled-error"
          label="Error"
          defaultValue="Hello World"
          variant="filled"
        />
        <TextField
          error
          id="filled-error-helper-text"
          label="Error"
          defaultValue="Hello World"
          helperText="Incorrect entry."
          variant="filled"
        />
      </div>
      <div>
        <TextField
          error
          id="standard-error"
          label="Error"
          defaultValue="Hello World"
          variant="standard"
        />
        <TextField
          error
          id="standard-error-helper-text"
          label="Error"
          defaultValue="Hello World"
          helperText="Incorrect entry."
          variant="standard"
        />
      </div>
    </Box>
  );
}