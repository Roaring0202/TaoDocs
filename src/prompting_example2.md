```import bittensor as bt
from langchain.memory import ConversationBufferMemory
from langchain.chains import ConversationChain

llm = bt.BittensorLLM(wallet_name="default")

conversation = ConversationChain(
    llm=llm,
    verbose=True,
    memory=ConversationBufferMemory()
)

conversation.predict('what is the capitol of Texas?')```

