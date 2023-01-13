# Fundamentos do TypeScript 

Projeto Desenvolvido pela RocketSeat<br>

Na base de ensino na Trilha Especializar: Fundamentos do TypeScript<br>

# Projeto 
Link do repositório:

https://github.com/rocketseat-education/lista_presenca/tree/typescript

# Clonando o projeto:
git clone https://github.com/rocketseat-education/lista_presenca.git

# Acessando diretório:
cd lista_presenca

# Instalando as dependências:
npm install

# Executando o projeto:
npm run dev

# Adicionando TypeScript
Instalando o TypeScript no projeto:
npm install --typescript --save-dev

# Arquivo json;
tsconfig.json

{
  "compilerOptions": {
    "target": "ESNext",
    "useDefineForClassFields": true,
    "lib": [
      "DOM",
      "DOM.Iterable",
      "ESNext"
    ],
    "allowJs": false,
    "skipLibCheck": false,
    "esModuleInterop": false,
    "allowSyntheticDefaultImports": true,
    "strict": true,
    "forceConsistentCasingInFileNames": true,
    "module": "ESNext",
    "moduleResolution": "Node",
    "resolveJsonModule": true,
    "isolatedModules": true,
    "noEmit": true,
    "jsx": "react-jsx"
  },
  "include": [
    "./src"
  ]
}

# Renomeando 

arquivo index.jsx para index.tsx na pasta Card;

# Tipando Componente

Definindo tipagens para o componente Card:

import './styles.css';

type CardProps = {
  name: string;
  time: string;
}

export function Card(props: CardProps) {
  return (
    <div className="card">
      <strong>{props.name}</strong>
      <small>{props.time}</small>
    </div>
  )
}

# Instalando o @types do react

npm i --save-dev @types/react

# Renomeando 
arquivo index.jsx para index.tsx na pasta Home;

# Tipando Estados
Para tipar os estados precisamos exportar o type do nosso componente Card.

export type CardProps = {
  name: string;
  time: string;
}

# Após a exportação, precisamos importar em nosso arquivo Home.tsx

import { Card, CardProps } from '../../components/Card';
E em seguida, passar as propriedades para o nosso estado:

const [students, setStudents] = useState<CardProps[]>([]);


# Tipando resposta da API
Para a tipagem de resposta da API precisamos criar dois types

type ProfileResponse = {
  name: string;
  avatar_url: string;
}

type User = {
  name: string;
  avatar: string;
}
Importar as propriedades do nosso type no useEffect():

useEffect(() => {
    async function fetchData() {
      const response = await fetch('https://api.github.com/users/rodrigorgtic');
      const data = await response.json() as ProfileResponse;

      setUser({
        name: data.name,
        avatar: data.avatar_url,
      });
    }

    fetchData();
  }, []);
  
E modificar o nosso estado:

const [students, setStudents] = useState<CardProps[]>([]);