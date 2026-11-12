
# Linux Desktop Development Environment

Ambiente de desenvolvimento para criação de aplicativos desktop Linux modernos, utilizando Python, GTK4, Libadwaita e tecnologias do ecossistema GNOME.

O objetivo deste ambiente é oferecer uma base organizada para desenvolver aplicativos Linux nativos, com interfaces modernas, componentes reutilizáveis, identidade visual consistente e distribuição por Flatpak.

---

## 1. Sobre o projeto

Este ambiente reúne ferramentas e bibliotecas para desenvolver:

- Aplicativos desktop Linux.
- Gerenciadores de arquivos.
- Lojas de aplicativos.
- Dashboards e ferramentas de sistema.
- Aplicativos de produtividade.
- Players de áudio e vídeo.
- Utilitários para GNOME.
- Aplicativos com interfaces personalizadas.

A stack principal utiliza:

- Python 3
- PyGObject
- GTK4
- Libadwaita
- Blueprint Compiler
- GTK CSS
- Flatpak
- Flatpak Builder
- GNOME Builder
- Rust
- C / C++
- Qt6 / QML (alternativa)

O ambiente foi planejado inicialmente para Zorin OS 18 e Ubuntu 24.04 LTS.

---

# 2. Arquitetura principal

A arquitetura recomendada é:

Python
  |
  v
PyGObject
  |
  v
GTK4 + Libadwaita
  |
  v
Blueprint + GTK CSS + SVG
  |
  v
Flatpak Builder
  |
  v
Aplicativo Linux

### Responsabilidade das tecnologias

| Tecnologia | Finalidade |
|---|---|
| Python | Lógica e funcionalidades |
| PyGObject | Integração Python com GNOME |
| GTK4 | Interface gráfica |
| Libadwaita | Componentes e padrões visuais GNOME |
| Blueprint | Definição declarativa de interfaces |
| GTK CSS | Personalização visual |
| SVG | Ícones e recursos vetoriais |
| Flatpak | Distribuição e isolamento |
| Meson | Sistema de build |
| Ninja | Execução de builds |
| Rust | Desenvolvimento complementar |
| Qt6 / QML | Interfaces alternativas |

---

# 3. Requisitos

Sistema recomendado:

- Zorin OS 18
- Ubuntu 24.04 LTS
- Distribuições baseadas em Ubuntu 24.04

Hardware recomendado:

- Processador dual-core ou superior.
- 8 GB de RAM.
- 10 GB de espaço livre.
- Ambiente gráfico GNOME ou compatível.

Softwares recomendados:

- Visual Studio Code
- GNOME Builder
- Git
- Terminal Linux

---

# 4. Atualização do sistema

Antes de instalar as dependências:

```bash
sudo apt update
sudo apt full-upgrade -y
sudo apt autoremove -y
```

Instale ferramentas básicas:

```bash
sudo apt install -y \
  software-properties-common \
  ca-certificates \
  curl \
  wget \
  git \
  git-lfs \
  unzip \
  zip \
  build-essential
```

---

# 5. Ferramentas de compilação

Instale os compiladores e ferramentas de desenvolvimento:

```bash
sudo apt install -y \
  gcc \
  g++ \
  clang \
  lld \
  lldb \
  gdb \
  make \
  cmake \
  meson \
  ninja-build \
  pkg-config \
  autoconf \
  automake \
  libtool \
  gettext \
  jq \
  ripgrep \
  tree \
  htop \
  btop \
  shellcheck \
  valgrind
```

Essas ferramentas são utilizadas para compilar, depurar e construir aplicativos.

---

# 6. Instalação do Python

Instale Python e suas ferramentas:

```bash
sudo apt install -y \
  python3 \
  python3-dev \
  python3-venv \
  python3-pip \
  python3-setuptools \
  python3-wheel \
  pipx
```

Configure o pipx:

```bash
pipx ensurepath
```

O pipx permite instalar ferramentas Python isoladamente do ambiente principal do sistema.

---

# 7. Instalação do GTK4 e Libadwaita

Esta é a principal stack gráfica do ambiente.

Instale as bibliotecas:

```bash
sudo apt install -y \
  libgtk-4-dev \
  libadwaita-1-dev \
  libglib2.0-dev \
  libgirepository1.0-dev \
  libgraphene-1.0-dev \
  libcairo2-dev \
  libpango1.0-dev \
  libgdk-pixbuf-2.0-dev \
  libepoxy-dev \
  libgtksourceview-5-dev \
  libflatpak-dev \
  libappstream-dev \
  libxml2-dev \
  libjson-glib-dev \
  libcurl4-openssl-dev
```

Instale os bindings Python:

```bash
sudo apt install -y \
  python3-gi \
  python3-gi-cairo \
  gir1.2-gtk-4.0 \
  gir1.2-adw-1 \
  gobject-introspection
```

Essas dependências permitem desenvolver interfaces GTK4 diretamente em Python.

---

# 8. Blueprint Compiler

Blueprint é uma linguagem declarativa utilizada para construir interfaces GTK.

Instalação:

```bash
sudo apt install -y blueprint-compiler
```

Verificação:

```bash
blueprint-compiler --version
```

Os arquivos Blueprint utilizam a extensão:

```text
.blp
```

Eles permitem organizar a estrutura visual das aplicações separadamente da lógica Python.

---

# 9. Instalação do Rust

Rust é uma linguagem complementar para desenvolver componentes de alto desempenho.

Instalação:

```bash
curl --proto '=https' --tlsv1.2 -sSf \
https://sh.rustup.rs | sh
```

Carregue o ambiente:

```bash
source "$HOME/.cargo/env"
```

Atualize:

```bash
rustup update
```

Instale ferramentas:

```bash
rustup component add rustfmt clippy rust-analyzer
```

Verifique:

```bash
rustc --version
cargo --version
```

Bibliotecas recomendadas:

- gtk4-rs
- libadwaita-rs
- Relm4
- GLib
- GIO
- Serde
- Tokio

Documentação:

https://gtk-rs.org/

https://relm4.org/

https://lib.rs/crates/libadwaita

---

# 10. Instalação do Flatpak

Flatpak é a principal tecnologia recomendada para distribuir os aplicativos.

Instale:

```bash
sudo apt install -y \
  flatpak \
  flatpak-builder \
  elfutils \
  desktop-file-utils \
  appstream \
  appstream-util
```

Adicione o Flathub:

```bash
sudo flatpak remote-add --if-not-exists flathub \
https://flathub.org/repo/flathub.flatpakrepo
```

Instale o GNOME Builder:

```bash
flatpak install -y flathub org.gnome.Builder
```

Execute:

```bash
flatpak run org.gnome.Builder
```

O Flatpak Builder permite criar pacotes isolados com dependências e runtimes específicos.

Documentação:

https://docs.flatpak.org/

https://docs.flatpak.org/en/latest/flatpak-builder.html

---

# 11. Instalação das ferramentas gráficas

Para criar ícones, ilustrações e recursos visuais:

```bash
sudo apt install -y \
  inkscape \
  gimp \
  fonts-inter \
  fonts-noto-core \
  fonts-noto-color-emoji \
  fonts-firacode \
  fonts-jetbrains-mono
```

Ferramentas recomendadas:

| Aplicativo | Utilização |
|---|---|
| Inkscape | SVG e iconografia |
| GIMP | Edição de imagens |
| Penpot | Prototipagem e Design System |
| GNOME Builder | Desenvolvimento GNOME |
| VS Code | Desenvolvimento geral |

Penpot:

https://penpot.app/

Inkscape:

https://inkscape.org/

GIMP:

https://www.gimp.org/

---

# 12. Bibliotecas adicionais

Instale bibliotecas utilizadas em aplicações mais completas:

```bash
sudo apt install -y \
  libsqlite3-dev \
  libsecret-1-dev \
  libsoup-3.0-dev \
  libnotify-dev \
  libportal-dev \
  libgstreamer1.0-dev \
  libgstreamer-plugins-base1.0-dev \
  libpipewire-0.3-dev \
  libpulse-dev \
  libssl-dev \
  libarchive-dev \
  libpoppler-glib-dev
```

Essas dependências permitem trabalhar com:

- Banco de dados SQLite.
- Gerenciamento de credenciais.
- Comunicação HTTP.
- Notificações.
- Integração com o desktop.
- Reprodução de mídia.
- Áudio.
- Arquivos PDF.
- Arquivos compactados.

Nem todos os projetos precisam de todas essas bibliotecas.

---

# 13. Qt6 e QML (opcional)

Para projetos que necessitem de interfaces altamente personalizadas:

```bash
sudo apt install -y \
  qt6-base-dev \
  qt6-base-dev-tools \
  qt6-declarative-dev \
  qt6-tools-dev \
  qt6-tools-dev-tools \
  qt6-wayland \
  qml6-module-qtquick \
  qml6-module-qtquick-controls \
  qml6-module-qtquick-layouts \
  qml6-module-qtquick-dialogs
```

Qt6 é uma alternativa à stack GTK4.

Documentação:

https://doc.qt.io/qt-6/

https://develop.kde.org/docs/getting-started/kirigami/

---

# 14. Configuração do Visual Studio Code

Extensões recomendadas:

```bash
code --install-extension ms-vscode.cpptools

code --install-extension ms-python.python

code --install-extension ms-python.vscode-pylance

code --install-extension rust-lang.rust-analyzer

code --install-extension ms-vscode.cmake-tools

code --install-extension tamasfe.even-better-toml

code --install-extension usernamehw.errorlens

code --install-extension eamodio.gitlens
```

Também é recomendado instalar extensões de suporte a Blueprint, Meson e Vala.

---

# 15. Criando o primeiro aplicativo

Crie a estrutura:

```bash
mkdir -p ~/Projetos/meu-aplicativo
cd ~/Projetos/meu-aplicativo
```

Crie o arquivo:

```bash
nano main.py
```

Adicione:

```python
import gi

gi.require_version("Gtk", "4.0")
gi.require_version("Adw", "1")

from gi.repository import Gtk, Adw


class MyApp(Adw.Application):

    def __init__(self):
        super().__init__(
            application_id="com.example.MyApp"
        )

    def do_activate(self):

        window = Adw.ApplicationWindow(
            application=self
        )

        window.set_title("Meu aplicativo Linux")
        window.set_default_size(900, 600)

        header = Adw.HeaderBar()

        title = Gtk.Label(
            label="Meu aplicativo"
        )

        header.set_title_widget(title)

        content = Gtk.Box(
            orientation=Gtk.Orientation.VERTICAL,
            spacing=18
        )

        content.set_margin_top(24)
        content.set_margin_bottom(24)
        content.set_margin_start(24)
        content.set_margin_end(24)

        heading = Gtk.Label(
            label="Bem-vindo!"
        )

        heading.add_css_class("title-1")

        description = Gtk.Label(
            label="Python + GTK4 + Libadwaita"
        )

        button = Gtk.Button(
            label="Começar"
        )

        button.add_css_class("suggested-action")

        content.append(heading)
        content.append(description)
        content.append(button)

        layout = Gtk.Box(
            orientation=Gtk.Orientation.VERTICAL
        )

        layout.append(header)
        layout.append(content)

        window.set_content(layout)
        window.present()


app = MyApp()
app.run()
```

Execute:

```bash
python3 main.py
```

---

# 16. Criando ambientes virtuais Python

Cada projeto deve possuir seu próprio ambiente virtual quando utilizar dependências Python adicionais.

Exemplo:

```bash
cd ~/Projetos/meu-aplicativo

python3 -m venv .venv

source .venv/bin/activate
```

Instale dependências:

```bash
pip install requests
```

Para sair:

```bash
deactivate
```

Importante:

Os bindings PyGObject instalados pelo sistema devem continuar disponíveis pelo Python do sistema. Não instale indiscriminadamente PyGObject pelo pip em ambientes virtuais.

---

# 17. Estrutura recomendada dos projetos

Estrutura sugerida:

```text
meu-aplicativo/
│
├── main.py
│
├── app/
│   ├── __init__.py
│   ├── application.py
│   ├── window.py
│   │
│   ├── views/
│   │   ├── home.py
│   │   ├── settings.py
│   │   └── about.py
│   │
│   ├── components/
│   │   ├── buttons.py
│   │   ├── cards.py
│   │   └── navigation.py
│   │
│   ├── services/
│   │   ├── database.py
│   │   └── system.py
│   │
│   └── resources/
│       ├── styles/
│       ├── icons/
│       └── images/
│
├── data/
│   ├── com.example.MyApp.desktop
│   ├── com.example.MyApp.metainfo.xml
│   └── icons/
│
├── packaging/
│   └── flatpak/
│
├── tests/
│
├── requirements.txt
├── pyproject.toml
├── README.md
└── LICENSE
```

Essa estrutura pode ser adaptada conforme o tamanho do aplicativo.

---

# 18. Distribuição dos aplicativos

Os principais formatos recomendados são:

| Formato | Utilização |
|---|---|
| Flatpak | Distribuição multiplataforma Linux |
| DEB | Ubuntu, Zorin e derivados compatíveis |
| AppImage | Aplicativos portáteis |

Para aplicativos GTK4 e Libadwaita, a recomendação principal é Flatpak utilizando o GNOME SDK.

Documentação:

https://docs.flatpak.org/

---

# 19. Verificação da instalação

Execute:

```bash
echo "===== PYTHON ====="
python3 --version

echo "===== RUST ====="
rustc --version
cargo --version

echo "===== GTK4 ====="
pkg-config --modversion gtk4

echo "===== LIBADWAITA ====="
pkg-config --modversion libadwaita-1

echo "===== GLIB ====="
pkg-config --modversion glib-2.0

echo "===== MESON ====="
meson --version

echo "===== NINJA ====="
ninja --version

echo "===== BLUEPRINT ====="
blueprint-compiler --version

echo "===== FLATPAK ====="
flatpak --version
```

Teste PyGObject:

```bash
python3 -c "import gi; print('PyGObject OK')"
```

Teste GTK4 e Libadwaita:

```bash
python3 -c "
import gi

gi.require_version('Gtk', '4.0')
gi.require_version('Adw', '1')

from gi.repository import Gtk, Adw

print('GTK:', Gtk.get_major_version())
print('Libadwaita:', Adw.get_major_version())
"
```

---

# 20. Design System e referências visuais

Para desenvolver interfaces modernas e consistentes, recomendamos estudar:

### GNOME

https://developer.gnome.org/hig/

https://gnome.pages.gitlab.gnome.org/libadwaita/

https://gitlab.gnome.org/GNOME/Incubator

### GTK

https://docs.gtk.org/gtk4/

https://pygobject.gnome.org/

### Blueprint

https://gnome.pages.gitlab.gnome.org/blueprint-compiler/

### KDE

https://develop.kde.org/hig/

### Iconografia

https://gitlab.gnome.org/GNOME/adwaita-icon-theme

https://lucide.dev/

https://inkscape.org/

### Design

https://penpot.app/

https://www.gimp.org/

---

# 21. Boas práticas

Para manter a qualidade dos aplicativos:

1. Utilize componentes Libadwaita sempre que possível.
2. Evite recriar componentes nativos sem necessidade.
3. Mantenha cores centralizadas em tokens.
4. Utilize SVG para iconografia.
5. Respeite os padrões tipográficos do GNOME.
6. Implemente suporte a temas claro e escuro.
7. Desenvolva interfaces adaptáveis.
8. Considere acessibilidade e contraste.
9. Reutilize componentes entre projetos.
10. Teste em diferentes resoluções e escalas.
11. Utilize Flatpak para distribuição.
12. Mantenha dependências organizadas.

---

# 22. Stack recomendada

A configuração principal deste ambiente é:

PYTHON
  |
  +-- PyGObject
  |
  +-- GTK4
  |
  +-- Libadwaita
  |
  +-- Blueprint
  |
  +-- GTK CSS
  |
  +-- SVG / Adwaita Icons
  |
  +-- Flatpak Builder

Tecnologias complementares:

- Rust
- C / C++
- Qt6
- QML
- SQLite
- GStreamer
- Meson
- Ninja

---

# 23. Objetivo do ambiente

Este ambiente foi preparado para servir como base de desenvolvimento de aplicativos desktop Linux modernos.

A prioridade é criar aplicações com:

- Interface visual profissional.
- Componentes consistentes.
- Identidade gráfica própria.
- Integração com o desktop.
- Boa performance.
- Código organizado.
- Facilidade de manutenção.
- Distribuição simplificada.

A stack GTK4 + Libadwaita é a escolha principal para aplicativos inspirados no GNOME e em projetos como Bazaar.

Python permite desenvolver rapidamente, enquanto Rust e C podem ser utilizados em componentes que necessitem de desempenho adicional.

---

## Licença

Defina aqui a licença escolhida para o repositório.

Exemplo: MIT License.

---

## Autor

Projeto comunitário de ambiente de desenvolvimento Linux.

Contribuições e melhorias são bem-vindas.
