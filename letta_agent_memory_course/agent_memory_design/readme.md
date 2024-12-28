## programming memory design: 

1. Storage of the core memory as the agent name, personal role and the associated parameters.
2. definition of the schema via the following format

3. pseudo memory description of model for each of the 


```python

from letta.schemas.memory import ChatMemory
from pydantic import BaseModel, Field
from typing import Optional, Dict


## along with describing 

class Block(BaseModel):
    value: str
    limit: int
    name: str
    template: bool
    label: str
    description: Optional[str] = None
    metadata_: Dict = Field(default_factory=dict)
    user_id: Optional[str] = None
    id: str

## defining the custom  functions to define for the agent memory:
## the following is the example of the taskMemory data structure that manages the tasks history based on the prompt defined and then runs when required tasks and then pop ups the other tasks.




class TaskMemory(ChatMemory): 

    def __init__(self, human: str, persona: str, tasks: List[str], _limit: int): 
        super().__init__(human=human, persona=persona, limit=_limit)
        self.link_block(
            name="tasks", 
            block=Block(
                limit=_limit, 
                value=json.dumps(tasks), 
                name="tasks_storage", 
                label="tasks"
            )
        )

    def tasks_queue_push()
        pass

```



