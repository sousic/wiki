#npm 패키지 만들기

#마지막 수정일
2016-11-16


#package 생성
    npm init
        -입력항목 예시
        name: (kr.huny.connect) 
        version: (1.0.0) 
        description: 
        entry point: (Gruntfile.js) 
        test command: 
        git repository: 
        keywords: 
        author: 
        license: (ISC) 
        About to write to /Users/sousic/my_web/kr.huny.connect/package.json:
        -출력항목 예시
        {
          "name": "kr.huny.connect",
          "version": "1.0.0",
          "description": "java micro dev site",
          "main": "Gruntfile.js",
          "dependencies": {
            "angular": "^1.5.8",
            "bootstrap": "^3.3.7",
            "font-awesome": "^4.7.0",
            "grunt-css": "^0.5.4",
            "grunt": "^1.0.1",
            "grunt-contrib-copy": "^1.0.0",
            "jquery.1": "^1.0.0",
            "jquery": "^3.1.1",
            "summernote": "^0.8.2"
          },
          "devDependencies": {},
          "scripts": {
            "test": "echo \"Error: no test specified\" && exit 1"
          },
          "author": "",
          "license": "ISC"
        }
        
        
        Is this ok? (yes) yes
