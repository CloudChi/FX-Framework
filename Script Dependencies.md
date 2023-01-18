# Dependencies Comparison

```mermaid
flowchart TB
  subgraph Module A
    subgraph Private
      subgraph Script A
      end
      subgraph Script B
      end
      subgraph Script C
      end      
    end
    subgraph Export
      subgraph Module B script A
      end
      subgraph Module B script B
      end
    end
  end
  
  subgraph Module B
  subgraph Stu
  end
  end
```
