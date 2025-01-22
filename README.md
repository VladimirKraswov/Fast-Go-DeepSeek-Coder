<p align="center">
<img width="1000px" alt="DeepSeek Coder" src="pictures/logo.png">
</p>
<p align="center"><a href="https://www.deepseek.com/">[<img src="pictures/home.png" width="20px"> Homepage]</a> | <a href="https://coder.deepseek.com/">[🤖 Chat with DeepSeek Coder]</a> | <a href="https://huggingface.co/deepseek-ai">[🤗 Models Download]</a> | <a href="https://discord.gg/Tc7c45Zzu5">[Discord]</a> | <a href="https://github.com/guoday/assert/blob/main/QR.png?raw=true">[WeChat (微信)]</a></p>
<p align="center">
  <a href="https://huggingface.co/papers/2401.14196"><b>Paper Link</b>👁️</a>
</p>
<hr>


### 1. Introduction of DeepSeek Coder

DeepSeek Coder — это серия моделей для работы с кодом, каждая из которых обучена с нуля на 2 триллионах токенов. Датасет состоит на **87% из кода** и на **13% из естественного языка** (английский и китайский).  

Мы предоставляем модели разного размера — от **1B до 33B** параметров. Каждая модель предварительно обучена на **коде проектного уровня**, используя **контекстное окно в 16K токенов** и дополнительную задачу **"заполнения пропусков"** (fill-in-the-blank). Это позволяет поддерживать **автодополнение кода** на уровне проекта и вставку недостающих фрагментов.  

С точки зрения возможностей программирования, **DeepSeek Coder демонстрирует передовые результаты среди open-source моделей для кода**, поддерживая **различные языки программирования** и превосходя конкурентов по многим бенчмаркам.

<p align="center">
<img src="pictures/result.png" alt="result" width="70%">
</p>

- **Огромный объем обучающих данных**: Обучена с нуля на **2 триллионах токенов**, включая **87% кода** и **13% языковых данных** на **английском и китайском** языках.  

- **Гибкость и масштабируемость**: Доступны модели **размером 1B, 5.7B, 6.7B и 33B**, позволяя пользователям выбрать наиболее подходящую конфигурацию под свои задачи.  

- **Передовая производительность модели**: Демонстрирует **лучшие результаты среди публичных моделей для работы с кодом** на бенчмарках **HumanEval, MultiPL-E, MBPP, DS-1000 и APPS**.  

- **Продвинутые возможности автодополнения кода**: Поддерживает **контекстное окно в 16K токенов** и задачу **заполнения пропусков (fill-in-the-blank)**, что обеспечивает **автодополнение кода на уровне всего проекта**.

#### Supported Programming Languages
`['ada', 'agda', 'alloy', 'antlr', 'applescript', 'assembly', 'augeas', 'awk', 'batchfile', 'bluespec', 'c', 'c-sharp', 'clojure', 'cmake', 'coffeescript', 'common-lisp', 'cpp', 'css', 'cuda', 'dart', 'dockerfile', 'elixir', 'elm', 'emacs-lisp', 'erlang', 'f-sharp', 'fortran', 'glsl', 'go', 'groovy', 'haskell', 'html', 'idris', 'isabelle', 'java', 'java-server-pages', 'javascript', 'json', 'julia', 'jupyter-notebook', 'kotlin', 'lean', 'literate-agda', 'literate-coffeescript', 'literate-haskell', 'lua', 'makefile', 'maple', 'markdown', 'mathematica', 'matlab', 'ocaml', 'pascal', 'perl', 'php', 'powershell', 'prolog', 'protocol-buffer', 'python', 'r', 'racket', 'restructuredtext', 'rmarkdown', 'ruby', 'rust', 'sas', 'scala', 'scheme', 'shell', 'smalltalk', 'solidity', 'sparql', 'sql', 'stan', 'standard-ml', 'stata', 'systemverilog', 'tcl', 'tcsh', 'tex', 'thrift', 'typescript', 'verilog', 'vhdl', 'visual-basic', 'xslt', 'yacc', 'yaml', 'zig']`

### **2. Результаты оценки**  

Мы оценили **DeepSeek Coder** на различных бенчмарках, связанных с программированием.  

Ниже представлены только результаты **`pass@1`** на тестах **HumanEval** (Python и мультиязычный), **MBPP** и **DS-1000**:

<p align="center">
<img src="pictures/table.png" alt="table" width="70%">
</p>


Результаты показывают, что **DeepSeek-Coder-Base-33B** значительно превосходит существующие **open-source** модели для работы с кодом. В сравнении с **CodeLlama-34B**, наша модель показывает **прирост производительности** на **7.9% (HumanEval Python), 9.3% (HumanEval Multilingual), 10.8% (MBPP) и 5.9% (DS-1000)**.  

Удивительно, но **DeepSeek-Coder-Base-7B** достигает уровня производительности **CodeLlama-34B**.  

После **обучения на инструкциях (instruction tuning)**, модель **DeepSeek-Coder-Instruct-33B** демонстрирует **лучшие результаты, чем GPT-3.5-turbo** на **HumanEval** и показывает **сопоставимые результаты с GPT-3.5-turbo** на **MBPP**.  

Более подробную информацию об оценке можно найти в... *(здесь, вероятно, должна быть ссылка или продолжение текста).*[Detailed Evaluation](#6-detailed-evaluation-results).


### **3. Процесс создания данных и обучения модели**  

#### **Создание данных**  

- Шаг 1: Сбор данных кода из **GitHub** с применением тех же правил фильтрации, что и... *(здесь, вероятно, должна быть ссылка или упоминание другой модели или методологии).* [StarCoder Data](https://github.com/bigcode-project/bigcode-dataset) to filter data.
- Шаг 2: **Анализ зависимостей** файлов внутри одного репозитория и **перестановка** файлов в соответствии с их зависимостями.  
- Шаг 3: **Объединение зависимых файлов** в единый пример и использование **MinHash на уровне репозитория** для удаления дубликатов.  
- Шаг 4: **Дополнительная фильтрация** низкокачественного кода, включая файлы с **синтаксическими ошибками** и плохой читаемостью.

<img src="pictures/data_clean.png" alt="data_creation" width="100%">

#### Model Training

### **Процесс обучения модели**  

- Шаг 1: Начальное предобучение на датасете, состоящем из **87% кода, 10% языковых данных, связанных с кодом** (GitHub Markdown и StackExchange) и **3% не связанных с кодом китайских текстов**. На этом этапе модели обучаются на **1.8 триллиона токенов** с **контекстным окном в 4K**.  
- Шаг 2: Дополнительное предобучение с расширенным **контекстным окном в 16K** на **дополнительных 200 миллиардов токенов**, что приводит к созданию базовых моделей (**DeepSeek-Coder-Base**).  
- Шаг 3: Тонкая настройка (Instruction Fine-tuning) на **2 миллиардах токенов инструкционных данных**, что формирует **инструкционно-настроенные модели** (**DeepSeek-Coder-Instruct**).

<img src="pictures/model_pretraining.png" alt="model_pretraining" width="100%">


### **4. Как использовать**  
Прежде чем начать, необходимо установить все необходимые зависимости. Вы можете сделать это, выполнив следующую команду:
```
pip install -r requirements.txt
```
Демо-версия также доступна на сайте[🤗 Hugging Face Space](https://huggingface.co/spaces/deepseek-ai/deepseek-coder-33b-instruct), и вы можете запустить демонстрационную версию локально, используя `app.py` в [demo](https://github.com/deepseek-ai/deepseek-coder/tree/main/demo) папке.

Вот несколько примеров того, как использовать нашу модель.

#### 1) Code Completion (Дописывание кода)
```python
from transformers import AutoTokenizer, AutoModelForCausalLM
import torch
tokenizer = AutoTokenizer.from_pretrained("deepseek-ai/deepseek-coder-6.7b-base", trust_remote_code=True)
model = AutoModelForCausalLM.from_pretrained("deepseek-ai/deepseek-coder-6.7b-base", trust_remote_code=True, torch_dtype=torch.bfloat16).cuda()
input_text = "#write a quick sort algorithm"
inputs = tokenizer(input_text, return_tensors="pt").to(model.device)
outputs = model.generate(**inputs, max_length=128)
print(tokenizer.decode(outputs[0], skip_special_tokens=True))
```
This code will output the following result:
```
def quick_sort(arr):
    if len(arr) <= 1:
        return arr
    pivot = arr[0]
    left = []
    right = []
    for i in range(1, len(arr)):
        if arr[i] < pivot:
            left.append(arr[i])
        else:
            right.append(arr[i])
    return quick_sort(left) + [pivot] + quick_sort(right)
```

#### 2) Code Insertion (Вставка кода)
```python
from transformers import AutoTokenizer, AutoModelForCausalLM
import torch
tokenizer = AutoTokenizer.from_pretrained("deepseek-ai/deepseek-coder-6.7b-base", trust_remote_code=True)
model = AutoModelForCausalLM.from_pretrained("deepseek-ai/deepseek-coder-6.7b-base", trust_remote_code=True, torch_dtype=torch.bfloat16).cuda()
input_text = """<｜fim▁begin｜>def quick_sort(arr):
    if len(arr) <= 1:
        return arr
    pivot = arr[0]
    left = []
    right = []
<｜fim▁hole｜>
        if arr[i] < pivot:
            left.append(arr[i])
        else:
            right.append(arr[i])
    return quick_sort(left) + [pivot] + quick_sort(right)<｜fim▁end｜>"""
inputs = tokenizer(input_text, return_tensors="pt").to(model.device)
outputs = model.generate(**inputs, max_length=128)
print(tokenizer.decode(outputs[0], skip_special_tokens=True)[len(input_text):])
```
This code will output the following result:
```
   for i in range(1, len(arr)):
```

#### 3) Chat Model Inference (Работа в режиме чата)
```python
from transformers import AutoTokenizer, AutoModelForCausalLM
import torch
tokenizer = AutoTokenizer.from_pretrained("deepseek-ai/deepseek-coder-6.7b-instruct", trust_remote_code=True)
model = AutoModelForCausalLM.from_pretrained("deepseek-ai/deepseek-coder-6.7b-instruct", trust_remote_code=True, torch_dtype=torch.bfloat16).cuda()
messages=[
    { 'role': 'user', 'content': "write a quick sort algorithm in python."}
]
inputs = tokenizer.apply_chat_template(messages, add_generation_prompt=True, return_tensors="pt").to(model.device)
# tokenizer.eos_token_id is the id of <|EOT|> token
outputs = model.generate(inputs, max_new_tokens=512, do_sample=False, top_k=50, top_p=0.95, num_return_sequences=1, eos_token_id=tokenizer.eos_token_id)
print(tokenizer.decode(outputs[0][len(inputs[0]):], skip_special_tokens=True))
```
This code will output the following result:
```
Sure, here is a simple implementation of the Quick Sort algorithm in Python:

def quick_sort(arr):
    if len(arr) <= 1:
        return arr
    else:
        pivot = arr[0]
        less_than_pivot = [x for x in arr[1:] if x <= pivot]
        greater_than_pivot = [x for x in arr[1:] if x > pivot]
        return quick_sort(less_than_pivot) + [pivot] + quick_sort(greater_than_pivot)

# Test the function
arr = [10, 7, 8, 9, 1, 5]
print("Original array:", arr)
print("Sorted array:", quick_sort(arr))

Этот алгоритм работает, выбирая **опорный (pivot)** элемент из массива и разделяя остальные элементы на два подмассива в зависимости от того, меньше они или больше опорного. Затем **опорный элемент занимает свою окончательную позицию** в отсортированном массиве. Процесс рекурсивно повторяется для полученных подмассивов.
```

Если вы не хотите использовать предоставленный API `apply_chat_template`, который загружает шаблон из `tokenizer_config.json`, вы можете использовать следующий шаблон для общения с нашей моделью.  

Замените `['content']` на ваши инструкции и предыдущие (если есть) ответы модели. Затем модель сгенерирует ответ на текущую инструкцию.
```
Вы — AI-ассистент по программированию, использующий модель **DeepSeek Coder**, разработанную компанией **DeepSeek**. Вы отвечаете **только на вопросы, связанные с компьютерными науками**.  

На **политически чувствительные темы, вопросы безопасности, конфиденциальности и другие не относящиеся к компьютерным наукам вопросы** — вы **откажетесь отвечать**.
### Инструкции:
['content']
### Ответ:
['content']
<|EOT|>
### Инструкции:
['content']
### Ответ:

```

#### 4) Repository Level Code Completion (Завершение кода на уровне репозитория)
```python
from transformers import AutoTokenizer, AutoModelForCausalLM
import torch
tokenizer = AutoTokenizer.from_pretrained("deepseek-ai/deepseek-coder-6.7b-base", trust_remote_code=True)
model = AutoModelForCausalLM.from_pretrained("deepseek-ai/deepseek-coder-6.7b-base", trust_remote_code=True, torch_dtype=torch.bfloat16).cuda()

input_text = """#utils.py
import torch
from sklearn import datasets
from sklearn.model_selection import train_test_split
from sklearn.preprocessing import StandardScaler
from sklearn.metrics import accuracy_score

def load_data():
    iris = datasets.load_iris()
    X = iris.data
    y = iris.target

    # Standardize the data
    scaler = StandardScaler()
    X = scaler.fit_transform(X)

    X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.3, random_state=42)

    # Convert numpy data to PyTorch tensors
    X_train = torch.tensor(X_train, dtype=torch.float32)
    X_test = torch.tensor(X_test, dtype=torch.float32)
    y_train = torch.tensor(y_train, dtype=torch.int64)
    y_test = torch.tensor(y_test, dtype=torch.int64)

    return X_train, X_test, y_train, y_test

def evaluate_predictions(y_test, y_pred):
    return accuracy_score(y_test, y_pred)


# model.py
import torch
import torch.nn as nn
import torch.optim as optim
from torch.utils.data import DataLoader, TensorDataset

class IrisClassifier(nn.Module):
    def __init__(self):
        super(IrisClassifier, self).__init__()
        self.fc = nn.Sequential(
            nn.Linear(4, 16),
            nn.ReLU(),
            nn.Linear(16, 3)
        )

    def forward(self, x):
        return self.fc(x)

    def train_model(self, X_train, y_train, epochs, lr, batch_size):
        criterion = nn.CrossEntropyLoss()
        optimizer = optim.Adam(self.parameters(), lr=lr)

        # Create DataLoader for batches
        dataset = TensorDataset(X_train, y_train)
        dataloader = DataLoader(dataset, batch_size=batch_size, shuffle=True)

        for epoch in range(epochs):
            for batch_X, batch_y in dataloader:
                optimizer.zero_grad()
                outputs = self(batch_X)
                loss = criterion(outputs, batch_y)
                loss.backward()
                optimizer.step()

    def predict(self, X_test):
        with torch.no_grad():
            outputs = self(X_test)
            _, predicted = outputs.max(1)
        return predicted.numpy()


# main.py
from utils import load_data, evaluate_predictions
from model import IrisClassifier as Classifier

def main():
    # Model training and evaluation
"""
inputs = tokenizer(input_text, return_tensors="pt").to(model.device)
outputs = model.generate(**inputs, max_new_tokens=140)
print(tokenizer.decode(outputs[0]))
```

---
В следующем сценарии модель **DeepSeek-Coder-6.7B** эффективно использует класс **IrisClassifier** и его методы из файла `model.py`, а также функции из файла `utils.py`, чтобы правильно завершить реализацию **основной (main)** функции в файле `main.py` для обучения и оценки модели.

![Completion GIF](pictures/completion_demo.gif)

### 5. How to Fine-tune DeepSeek-Coder

Мы предоставляем скрипт **`finetune/finetune_deepseekcoder.py`** для пользователей, чтобы они могли дообучать наши модели для специфических задач.  

Этот скрипт поддерживает обучение с использованием **[DeepSpeed](https://github.com/microsoft/DeepSpeed)**.  

Для установки необходимых пакетов выполните следующую команду:

```bash
pip install -r finetune/requirements.txt
```

Пожалуйста, подготовьте ваши тренировочные данные в соответствии с форматом [Sample Dataset Format](https://huggingface.co/datasets/nickrosh/Evol-Instruct-Code-80k-v1).  

Каждая строка должна представлять собой **JSON-объект**, содержащий два обязательных поля:  
- **`instruction`** – инструкция для модели  
- **`output`** – ожидаемый ответ  

После подготовки данных вы можете использовать **пример shell-скрипта** для дообучения модели **`deepseek-ai/deepseek-coder-6.7b-instruct`**.  

**Важно:**  
- Укажите пути к файлам данных и выходному каталогу через переменные **`DATA_PATH`** и **`OUTPUT_PATH`**.  
- Подберите подходящие **гиперпараметры** (например, **`learning_rate`**, **`per_device_train_batch_size`**) в зависимости от вашей задачи.

```bash
DATA_PATH="<your_data_path>"
OUTPUT_PATH="<your_output_path>"
MODEL="deepseek-ai/deepseek-coder-6.7b-instruct"

cd finetune && deepspeed finetune_deepseekcoder.py \
    --model_name_or_path $MODEL_PATH \
    --data_path $DATA_PATH \
    --output_dir $OUTPUT_PATH \
    --num_train_epochs 3 \
    --model_max_length 1024 \
    --per_device_train_batch_size 16 \
    --per_device_eval_batch_size 1 \
    --gradient_accumulation_steps 4 \
    --evaluation_strategy "no" \
    --save_strategy "steps" \
    --save_steps 100 \
    --save_total_limit 100 \
    --learning_rate 2e-5 \
    --warmup_steps 10 \
    --logging_steps 1 \
    --lr_scheduler_type "cosine" \
    --gradient_checkpointing True \
    --report_to "tensorboard" \
    --deepspeed configs/ds_config_zero3.json \
    --bf16 True
```

### 6. Detailed Evaluation Results

The reproducible code for the following evaluation results can be found in the [Evaluation](https://github.com/deepseek-ai/deepseek-coder/tree/main/Evaluation) directory.
#### 1) Подробные результаты оценки
![HumanEval](pictures/HumanEval.png)

#### 2) MBPP Benchmark
<img src="pictures/MBPP.png" alt="MBPP" width="40%">

#### 3) DS-1000 Benchmark
![DS-1000](pictures/DS-1000.png)

#### 4) Program-Aid Math Reasoning Benchmark
![Math](pictures/Math.png)

### Вывод с помощью vLLM

You can also employ [vLLM](https://github.com/vllm-project/vllm) for high-throughput inference.

**Заполнение текста**

```python
from vllm import LLM, SamplingParams

tp_size = 4 # Tensor Parallelism
sampling_params = SamplingParams(temperature=0.7, top_p=0.9, max_tokens=100)
model_name = "deepseek-ai/deepseek-coder-6.7b-base"
llm = LLM(model=model_name, trust_remote_code=True, gpu_memory_utilization=0.9, tensor_parallel_size=tp_size)

prompts = [
    "If everyone in a country loves one another,",
    "The research should also focus on the technologies",
    "To determine if the label is correct, we need to"
]
outputs = llm.generate(prompts, sampling_params)

generated_text = [output.outputs[0].text for output in outputs]
print(generated_text)
```

**авершение общения в чате**

```python
from transformers import AutoTokenizer
from vllm import LLM, SamplingParams

tp_size = 4 # Tensor Parallelism
sampling_params = SamplingParams(temperature=0.7, top_p=0.9, max_tokens=100)
model_name = "deepseek-ai/deepseek-coder-6.7b-instruct"
tokenizer = AutoTokenizer.from_pretrained(model_name)
llm = LLM(model=model_name, trust_remote_code=True, gpu_memory_utilization=0.9, tensor_parallel_size=tp_size)

messages_list = [
    [{"role": "user", "content": "Who are you?"}],
    [{"role": "user", "content": "What can you do?"}],
    [{"role": "user", "content": "Explain Transformer briefly."}],
]
prompts = [tokenizer.apply_chat_template(messages, add_generation_prompt=True, tokenize=False) for messages in messages_list]

sampling_params.stop = [tokenizer.eos_token]
outputs = llm.generate(prompts, sampling_params)

generated_text = [output.outputs[0].text for output in outputs]
print(generated_text)
```

### 7. Q&A

#### **Можете ли вы предоставить файл `tokenizer.model` для квантования модели?**  

**DeepSeek Coder** использует **[HuggingFace Tokenizer](https://huggingface.co/docs/tokenizers/index)** для реализации **Bytelevel-BPE** алгоритма, с специально разработанными **пред-токенизаторами**, обеспечивающими оптимальную производительность.  

На данный момент **не существует** прямого способа конвертации **HuggingFace Tokenizer** в **SentencePiece Tokenizer**.  

Мы работаем над **открытыми методами квантования**, чтобы упростить использование **HuggingFace Tokenizer** в задачах квантования.

##### GGUF(llama.cpp)

Мы отправили **[Pull Request (PR)](https://github.com/ggerganov/llama.cpp/pull/4070)** в популярный репозиторий квантования **[llama.cpp](https://github.com/ggerganov/llama.cpp)**, чтобы обеспечить **полную поддержку всех HuggingFace пред-токенизаторов**, включая наш.  

Пока **PR ожидает слияния**, вы можете **самостоятельно** сгенерировать свою **GGUF-модель**, выполнив следующие шаги:  

```bash
git clone https://github.com/DOGEwbx/llama.cpp.git
cd llama.cpp
git checkout regex_gpt2_preprocess
# set up the environment according to README
make
python3 -m pip install -r requirements.txt
# generate GGUF model
python convert-hf-to-gguf.py <MODEL_PATH> --outfile <GGUF_PATH> --model-name deepseekcoder
# use q4_0 quantization as an example
./quantize <GGUF_PATH> <OUTPUT_PATH> q4_0
./main -m <OUTPUT_PATH> -n 128 -p <PROMPT>
```
##### GPTQ(exllamav2)

### **Обновление:**  
**[exllamav2](https://github.com/turboderp/exllamav2)** теперь поддерживает **HuggingFace Tokenizer**.  
Пожалуйста, **обновите до последней версии** и попробуйте его в работе.  

⚠ **Важно:** Установите **RoPE scaling** на **4**, чтобы получить корректный вывод. Дополнительное обсуждение можно найти в [этом PR](https://github.com/turboderp/exllamav2/pull/189).  

---

### **Как использовать deepseek-coder-instruct для автодополнения кода?**  

Хотя модели **deepseek-coder-instruct** **не обучались специально** для задач автодополнения кода в процессе **Supervised Fine-Tuning (SFT)**, они **сохранили эту способность**.  

Чтобы **активировать автодополнение**, необходимо изменить параметр **`eos_token_id`**:  
- Установите **`eos_token_id = 32014`**, вместо стандартного значения **`32021`** в конфигурации **deepseek-coder-instruct**.  

Эта модификация позволяет **модели корректно распознавать конец последовательности**, что **улучшает работу с задачами автодополнения кода**.


### **8. Ресурсы**  
**[awesome-deepseek-coder](https://github.com/deepseek-ai/awesome-deepseek-coder)** — это подборка **open-source проектов**, связанных с **DeepSeek Coder**.  

---

### **9. Лицензия**  
Этот репозиторий с кодом распространяется по **MIT License**.  
Использование моделей **DeepSeek Coder** регулируется **Model License**, при этом **поддерживается коммерческое использование**.  

Более подробную информацию можно найти в файлах **[LICENSE-CODE](LICENSE-CODE)** и **[LICENSE-MODEL](LICENSE-MODEL)**.  

---

### **10. Цитирование**  
Если вы используете **DeepSeek Coder** в своих работах, пожалуйста, укажите следующую ссылку:  
```
@misc{deepseek-coder,
  author = {Daya Guo, Qihao Zhu, Dejian Yang, Zhenda Xie, Kai Dong, Wentao Zhang, Guanting Chen, Xiao Bi, Y. Wu, Y.K. Li, Fuli Luo, Yingfei Xiong, Wenfeng Liang},
  title = {DeepSeek-Coder: When the Large Language Model Meets Programming -- The Rise of Code Intelligence},
  journal = {CoRR},
  volume = {abs/2401.14196},
  year = {2024},
  url = {https://arxiv.org/abs/2401.14196},
}
```

---

### **11. Контакты**  
Если у вас есть вопросы, создайте **issue** в репозитории или свяжитесь с нами по электронной почте:  
📩 **[service@deepseek.com](mailto:service@deepseek.com)**.