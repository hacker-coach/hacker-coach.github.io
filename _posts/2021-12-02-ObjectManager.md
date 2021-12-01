---
title: ObjectManager
published: true
---



```php
    protected function getObj($objPath){
        $objectManager = \Magento\Framework\App\ObjectManager::getInstance();
        return $objectManager->create($objPath);
    }
```
