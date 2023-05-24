# langchain-learn


## langchain 安装问题解决

### 1.`from langchain.llms import OpenAI` 报错：TypeError: issubclass() arg 1 must be a class


详细错误信息
```python
----> 1 from langchain.llms import OpenAI
      2 # from langchain.prompts impo
      3 import json

File f:\newAnaconda3\envs\langchain_python39\lib\site-packages\langchain\__init__.py:6
      3 from importlib import metadata
      4 from typing import Optional
----> 6 from langchain.agents import MRKLChain, ReActChain, SelfAskWithSearchChain
      7 from langchain.cache import BaseCache
      8 from langchain.chains import (
      9     ConversationChain,
     10     LLMBashChain,
   (...)
     18     VectorDBQAWithSourcesChain,
     19 )

File f:\newAnaconda3\envs\langchain_python39\lib\site-packages\langchain\agents\__init__.py:2
      1 """Interface for agents."""
----> 2 from langchain.agents.agent import (
      3     Agent,
      4     AgentExecutor,
      5     AgentOutputParser,
      6     BaseMultiActionAgent,
      7     BaseSingleActionAgent,
      8     LLMSingleActionAgent,
      9 )
     10 from langchain.agents.agent_toolkits import (
     11     create_csv_agent,
     12     create_json_agent,
   (...)
     21     create_vectorstore_router_agent,
     22 )
     23 from langchain.agents.agent_types import AgentType

File f:\newAnaconda3\envs\langchain_python39\lib\site-packages\langchain\agents\agent.py:16
     13 from pydantic import BaseModel, root_validator
     15 from langchain.agents.agent_types import AgentType
---> 16 from langchain.agents.tools import InvalidTool
     17 from langchain.base_language import BaseLanguageModel
     18 from langchain.callbacks.base import BaseCallbackManager

File f:\newAnaconda3\envs\langchain_python39\lib\site-packages\langchain\agents\tools.py:8
...
    851 if not isinstance(cls, _GenericAlias):
--> 852     return issubclass(cls, self.__origin__)
    853 return super().__subclasscheck__(cls)

TypeError: issubclass() arg 1 must be a class
```

解决方案：
https://github.com/hwchase17/langchain/issues/5113

安装以下两个包
```bash
typing-inspect==0.8.0
typing_extensions==4.5.0
```




