# API 使用示例

## JavaScript/TypeScript

```typescript
// 使用 axios 调用 API
import axios from 'axios';

const api = axios.create({
  baseURL: 'https://api.museum-cloud.com/v1',
  headers: {
    'Authorization': `Bearer ${token}`,
    'Content-Type': 'application/json'
  }
});

// 获取展品列表
async function getArtifacts(category?: string, page = 1, pageSize = 20) {
  const response = await api.get('/artifacts', {
    params: { category, page, pageSize }
  });
  return response.data;
}

// 创建新展品
async function createArtifact(artifact: {
  name: string;
  description?: string;
  category: string;
  imageUrls?: string[];
}) {
  const response = await api.post('/artifacts', artifact);
  return response.data;
}
```

## Python

```python
# 使用 requests 调用 API
import requests

class MuseumAPI:
    def __init__(self, token: str, base_url: str = 'https://api.museum-cloud.com/v1'):
        self.base_url = base_url
        self.headers = {
            'Authorization': f'Bearer {token}',
            'Content-Type': 'application/json'
        }
    
    def get_artifacts(self, category: str = None, page: int = 1, page_size: int = 20):
        params = {
            'category': category,
            'page': page,
            'pageSize': page_size
        }
        response = requests.get(
            f'{self.base_url}/artifacts',
            headers=self.headers,
            params={k: v for k, v in params.items() if v is not None}
        )
        return response.json()
    
    def create_artifact(self, name: str, category: str, description: str = None,
                       image_urls: list = None):
        data = {
            'name': name,
            'category': category,
            'description': description,
            'imageUrls': image_urls
        }
        response = requests.post(
            f'{self.base_url}/artifacts',
            headers=self.headers,
            json={k: v for k, v in data.items() if v is not None}
        )
        return response.json()
```