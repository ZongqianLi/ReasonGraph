# [ACL 2025 Demo] ReasonGraph: Visualisation of Reasoning Methods and Extended Inference Paths

<p align="center">
  <b>Language</b>
</p>

<p align="center">
  <a href="README.md">English</a> •
  <a href="README_CN.md">中文</a>
</p>

<p align="center">
  <b>Content</b>
</p>

<p align="center">
  <a href="#news">🚀 News</a> •
  <a href="#todo">✏️ Todo</a> •
  <a href="#introduction">✨ Introduction</a>
</p>

<p align="center">
  <a href="#examples">👀 Examples</a> •
  <a href="#quick use">🎨 Quick Use</a> •
  <a href="#environment">🖥️ Environment</a>
</p>

<p align="center">
  <a href="#citation">📌 Citation</a> •
  <a href="#license">🔖 License</a>
</p>

<p align="center">
  <b>Links</b>
</p>

<p align="center">
  <a href="https://huggingface.co/spaces/ZongqianLi/ReasonGraph">Online Demo</a> •
  <a href="https://arxiv.org/abs/2503.03979">Paper</a> •
  <a href="https://discord.gg/tA9DV7Fjzz">Discord</a> •
  <a href="https://forms.office.com/r/ebBSAKqHwj">Questionnaire</a>
</p>

<div id="news">&nbsp;</div>



## 🚀 News

- **[2025.05.23]** Accepted by ACL 2025 Demo!
- **[2025.03.24]** ⭐ Support visualisation of **long outputs** from **reasoning models**!!!
- **[2025.03.18]** Support more LLM providers and models. Support two languages, English and Chinese.
- **[2025.03.18]** Rate and provide comments in the [questionnaire](https://forms.office.com/r/ebBSAKqHwj) (takes about 30 seconds).
- **[2025.03.17]** Try the [online demo](https://huggingface.co/spaces/ZongqianLi/ReasonGraph) through Huggingface Page!
- **[2025.03.14]** Join our [Discord](https://discord.gg/tA9DV7Fjzz) group!
- **[2025.03.07]** The [paper](https://arxiv.org/abs/2503.03979) is available in Arxiv.
- **[2025.02.22]** Create the Github page.

<div>&nbsp;</div>
<div>&nbsp;</div>
<div id="todo">&nbsp;</div>



## ✏️ Todo & Help Wanted

<div>&nbsp;</div>
<div>&nbsp;</div>
<div id="introduction">&nbsp;</div>



## ✨ Introduction

**ReasonGraph** is an open-source web platform for visualizing and analyzing reasoning processes of Large Language Models (LLMs).

**Functions:**

- **Visualisation of Reasoning Paths:** Transforms text-format reasoning outputs into flow charts.
- **Long Reasoning:** Supports visualisation of extended outputs from reasoning models.
- **Meta Reasoning:** Provides built-in capabilities for models to self-select optimal reasoning methods.

**Characteristics:**

- **Model Support:** Integrates with over 50 state-of-the-art models from major LLM providers including Anthropic, OpenAI, Google, Grok, Deepseek, Qwen, and Together.AI.
- **Reasoning Methods:** Implements mainstream reasoning approaches including sequential methods and tree-based methods.
- **Modular Framework:** Standardized APIs for easy integration of new reasoning methods and models.
- **Beginner-Friendly:** Intuitive UI design with visualization updates and simple configuration.
- **Multilingual:** Support multi-languages and easy to be extended for more languages.

<div>&nbsp;</div>
<div>&nbsp;</div>
<div id="examples">&nbsp;</div>



## 👀 Examples

<details open>
<summary><strong>UI Screenshot:</strong></summary>

<p align="left">
  <img src="./figures/UI.png" width="100%">
</p>

</details>

<details open>
<summary><strong>Visualisation of outputs from reasoning models:</strong></summary>

Input: Give me two suggestions for transitioning from a journalist to a book editor? Use sequential and tree-based thinking and refinement loops.  
Model: deepseek-reasoner from DeepSeek

<p align="left">
  <img src="./figures/long_example.png" width="100%">
</p>

</details>

<div>&nbsp;</div>

<details open>
<summary><strong>Visualisation of sequential reasoning methods:</strong></summary>

Chain of Thoughts (top-left), Self-refine (top-middle), Least-to-most (top-right), Self-consistency (bottom-left):

<p align="left">
  <img src="./figures/sequence_example.png" width="80%">
</p>

</details>

<div>&nbsp;</div>

<details open>
<summary><strong>Visualisation of tree-based reasoning methods:</strong></summary>

Plain text (top), Beam Search (middle), Tree of Thoughts (bottom):

<p align="left">
  <img src="./figures/tree_example_2.png" width="80%">
</p>

</details>

<div>&nbsp;</div>
<div>&nbsp;</div>
<div id="quick use">&nbsp;</div>



## 🎨 Quick Use

<details open>
<summary><strong>Try the online demo:</strong></summary>

#### 1. Go to the website: https://huggingface.co/spaces/ZongqianLi/ReasonGraph

</details>

<div>&nbsp;</div>

<details>
<summary><strong>Visualize long outputs from reasoning models:</strong></summary>

#### 1. Select a reasoning model and enter its API key.

- API Provider: Deepseek; Model: deepseek-reasoner
- API Provider: Qwen; Model: qwq-plus

#### 2. Enter the API key for Claude.

#### 3. Click "Long Reasoning".

</details>

<div>&nbsp;</div>

<details>
<summary><strong>Install the package:</strong></summary>

#### 1. Set up the environment according to Section 🖥️ Environment below.

#### 2. Go to root directory:

<absolute_path>/ReasonGraph/

#### 3. Input the API key:

If you don't enter the API keys, the interface can still run normally, but you won't be able to use the corresponding models for inference.

<absolute_path>/ReasonGraph/api_keys.json

```
{
    "anthropic": "<to be filled>",
    "openai": "<to be filled>",
    "google": "<to be filled>",
    "together": "<to be filled>"
}
```

#### 4. Run the program with a single line of code in the terminal:

```
python app.py
```

#### 5. Open your browser and go to the local URL shown in the output.
```
 * Running on all addresses (X.X.X.X)
 * Running on http://XXX.X.X.X:XXXX
 * Running on http://XX.XXX.XXX.XXX:XXXX
```

</details>

<div>&nbsp;</div>
<div>&nbsp;</div>
<div id="environment">&nbsp;</div>



## 🖥️ Environment

```
python==3.11.8
requests==2.31.0
openai==1.63.2
together==1.4.1
flask==3.1.0
google==3.0.0
google-genai==1.2.0
google-generativeai==0.8.4
```

<div>&nbsp;</div>
<div>&nbsp;</div>
<div id="citation">&nbsp;</div>



## 📌 Citation

```
@misc{li2025reasongraphvisualisationreasoningpaths,
      title={ReasonGraph: Visualisation of Reasoning Paths}, 
      author={Zongqian Li and Ehsan Shareghi and Nigel Collier},
      year={2025},
      eprint={2503.03979},
      archivePrefix={arXiv},
      primaryClass={cs.CL},
      url={https://arxiv.org/abs/2503.03979}, 
}
```

<div>&nbsp;</div>
<div>&nbsp;</div>
<div id="license">&nbsp;</div>



## 🔖 License

```

```











