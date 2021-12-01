---
title: ObjectManager
published: true
---



```php
    protected function getObject($objPath){
        $objectManager = \Magento\Framework\App\ObjectManager::getInstance();
        return $objectManager->create($objPath);
    }
```
