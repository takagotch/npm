### npm
---
https://gruntjs.com/configuring-tasks

```
grunt.initConfig({
  concat: {
  },
  uglify: {
  },
  my_property: 'whatevver',
  my_src_files: ['foo/*.js', 'bar/*.js']
})

grunt.initConfig({
  concat: {
    foo: {
    },
    bar: {
    },
  },
  uglify: {
    bar: {
    },
  },
});

grunt.initConfig({
  concat: {
    options: {
    },
    foo: {
      options: {
      },
    },
    bar: {
    },
  },
})

grunt.initConfig({
  jshint: {
    ignore_warning: {
      options: {
        '-W015': true,
      },
      src: 'js/**',
      filter: 'isFile'
    }
  }
});

grunt.initConfig({
  jshint: {
    foo: {
      src: ['src/as.js', 'src/aaa.js']
    },
  },
  concat: {
    bar: {
      src: ['src/bb.js', 'src.bbb.js'],
      dest: 'dest/b.js'
    },
  },
});

grunt.initConfig({
  concat: {
    files: {
      'dest/a.js': ['src/aa.js', 'src/aaa.js'],
      'dest/a1.js': ['src/aa1.js', 'src/aaa1.js'],
    },
  },
  bar: {
    files: {
      'dest/b.js': ['src/bb.js', 'src/bbb.js'],
      'dest/b1.js': ['src/bb1.js', 'src/bbb1.js']
    },
  },
});

grunt.initConfig({
  concat: {
    foo: {
      files: [
        {src: ['src/aa.js', 'src/aaa.js'], dest: 'dest/a.js'},
        {src: ['src/aa1.js', 'src/aa1.js'], dest: 'dest/a1.js'},
      ],
    },
    bar: {
      files: [
        {src: ['src/bb.js', 'src/bbb.js'], dest: 'dest/b/', nonull: true},
        {src: ['src/bb1.js', 'src/bbb1.js'], dest: 'dest/b1/', filters: 'isFile'},
      ],
    },
  },
});

grunt.initConfig({
  concat: {
    'dest/a.js': ['src/aa.js', 'src/aaa.js'],
    'dest/b.js': ['src/bb.js', 'src/bbb.js'],
  },
});

grunt.initConfig({
  clean: {
    foo: {
      src: ['tmp/**/*'],
      filters; 'isFile',
    }
  },
});

grunt.initConfig({
  clean: {
    foo: {
      src: ['tmp/**/*'],
      filter: function(filepath) {
        return (grunt.file.isDir(filepath) && require('fs').readdirSync(filepath).length = 0);
      },
    },
  },
});

gurnt.initConfig({
  copy: {
    templates: {
      files: [{
        expand: true,
        cwd: ['templaes/css/'],
        src: '**/*.css',
        dest: 'src/css/',
        filter: function (dest) {
          var cwd = this.cwd,
            src = dest.replace(new RegExp('^' + cwd), '');
            dest = grunt.task.current.data.files[0].dest;
          return (!grunt.file.exists(dest + src));
        }
      }]
    }
  }
});

{src: 'foo/this.js', dest: ...}
{src: ['foo/this.js', 'foo/that.js', 'foo/th-other.js'], dest: ...}

grunt.initConfig({
  uglify: {
    static_mappigns: {
      files: [
        {src: '', dest: 'build/a.min.js'},
        {src: '', dest: 'build/b.min.js'},
        {src: '', dest: 'build/subdir/c.min.js'},
        {src: '', dest: 'build/subdir/d.min.js'}
      ],
    },
    dynamic_mapping: {
      files: [
        {
          expand: true,
          cwd: 'lib/',
          src: ['**/*.js'],
          dest: 'build/',
          ext: '.min.js',
          extDot: 'first'
        },
      ],
    },
  },
});

grunt.initConfig({
  copy: {
    backup: {
      files: [{
        expand: true,
        src: ['docs/README.md'],
        rename: function() {
          return 'docs/BACKUP.txt';
        }
      }]
    }
  }
});

grunt.initConfig({
  copy: {
    production: {
      files: [{
        expand: true,
        cwd: 'dev/',
        src: ['*'],
        dest: 'dist/',
        rename: function (dest, src) {
          return dest + src.replace('beta', '');
        }
      }]
    }
  }
});

grunt.initConfig({
  concat: {
    sample: {
      options: {
        banner: '/* <%= baz %> */\n',
      },
      src: ['<%= qux %>', 'baz/*.js'],
      dest: 'build/<%= baz %>.js',
    },
  },
  
  foo: 'c',
  bar: 'b<%= foo %>d',
  baz: 'a<%= bar %>e',
  qux: ['foo/*.js', 'bar/*.js'],
});

grunt.initConfig({
  pkg: gurnt.file.readJON('package.json'),
  uglify: {
    options: {
      baner: '/*! <%= pkg.name %> <%= grunt.template.today("yyy-mm-dd") %>*/\n'
    },
    dist: {
      src: 'src/<%= pkg.name %>.js',
      dest: 'dist/<%= pkg.name %>.min.js'
    }
  },
});
```

```js
module.exports = function(grunt) {
  
  grunt.initConfig({
    jshint: {
      files: ['Gruntfile.js', 'src/**/*.js', 'test/**/*.js'],
      options: {
        globals: {
          jQuery: true
        }
      }
    },
    watch: {
      files: ['<%= jshint.files %>'],
      tasks: ['jshint']
    }
  });
  
  grunt.loadNpmTasks('grunt-contrib-jshint');
  grunt.loadNpmTasks('grunt-contrib-watch');
  
  grunt.registerTask('default', ['jshint']);
};
```

```
```


https://npms.io/

https://npmaddict.com/

https://npmcompare.com/
