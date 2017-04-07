# api documentation for  [np (v2.13.1)](https://github.com/sindresorhus/np#readme)  [![npm package](https://img.shields.io/npm/v/npmdoc-np.svg?style=flat-square)](https://www.npmjs.org/package/npmdoc-np) [![travis-ci.org build-status](https://api.travis-ci.org/npmdoc/node-npmdoc-np.svg)](https://travis-ci.org/npmdoc/node-npmdoc-np)
#### A better `npm publish`

[![NPM](https://nodei.co/npm/np.png?downloads=true)](https://www.npmjs.com/package/np)

[![apidoc](https://npmdoc.github.io/node-npmdoc-np/build/screenCapture.buildNpmdoc.browser._2Fhome_2Ftravis_2Fbuild_2Fnpmdoc_2Fnode-npmdoc-np_2Ftmp_2Fbuild_2Fapidoc.html.png)](https://npmdoc.github.io/node-npmdoc-np/build/apidoc.html)

![npmPackageListing](https://npmdoc.github.io/node-npmdoc-np/build/screenCapture.npmPackageListing.svg)

![npmPackageDependencyTree](https://npmdoc.github.io/node-npmdoc-np/build/screenCapture.npmPackageDependencyTree.svg)



# package.json

```json

{
    "author": {
        "name": "Sindre Sorhus",
        "email": "sindresorhus@gmail.com",
        "url": "sindresorhus.com"
    },
    "bin": {
        "np": "cli.js"
    },
    "bugs": {
        "url": "https://github.com/sindresorhus/np/issues"
    },
    "dependencies": {
        "any-observable": "^0.2.0",
        "chalk": "^1.1.3",
        "del": "^2.2.0",
        "execa": "^0.6.3",
        "has-yarn": "^1.0.0",
        "inquirer": "^3.0.6",
        "listr": "^0.11.0",
        "log-symbols": "^1.0.2",
        "meow": "^3.7.0",
        "read-pkg-up": "^2.0.0",
        "rxjs": "^5.0.0-beta.9",
        "semver": "^5.1.0",
        "split": "^1.0.0",
        "stream-to-observable": "^0.2.0",
        "update-notifier": "^2.1.0"
    },
    "description": "A better 'npm publish'",
    "devDependencies": {
        "ava": "*",
        "xo": "*"
    },
    "directories": {},
    "dist": {
        "shasum": "1da79a7b37743dfca76d787c9cea4331b94cf03c",
        "tarball": "https://registry.npmjs.org/np/-/np-2.13.1.tgz"
    },
    "engines": {
        "node": ">=4"
    },
    "files": [
        "index.js",
        "cli.js",
        "lib"
    ],
    "gitHead": "27239a817211878c0d141e96426ed1c01d98c31c",
    "homepage": "https://github.com/sindresorhus/np#readme",
    "keywords": [
        "cli-app",
        "cli",
        "npm",
        "publish",
        "git",
        "push",
        "version",
        "bump",
        "commit"
    ],
    "license": "MIT",
    "maintainers": [
        {
            "name": "samverschueren",
            "email": "sam.verschueren@gmail.com"
        },
        {
            "name": "sindresorhus",
            "email": "sindresorhus@gmail.com"
        }
    ],
    "name": "np",
    "optionalDependencies": {},
    "readme": "ERROR: No README data found!",
    "repository": {
        "type": "git",
        "url": "git+https://github.com/sindresorhus/np.git"
    },
    "scripts": {
        "test": "xo && ava"
    },
    "version": "2.13.1",
    "xo": {
        "esnext": true
    }
}
```



# <a name="apidoc.tableOfContents"></a>[table of contents](#apidoc.tableOfContents)

#### [module np](#apidoc.module.np)
1.  object <span class="apidocSignatureSpan">np.</span>util
1.  object <span class="apidocSignatureSpan">np.</span>version

#### [module np.util](#apidoc.module.np.util)
1.  [function <span class="apidocSignatureSpan">np.util.</span>readPkg ()](#apidoc.element.np.util.readPkg)

#### [module np.version](#apidoc.module.np.version)
1.  [function <span class="apidocSignatureSpan">np.version.</span>getNewVersion (oldVersion, input)](#apidoc.element.np.version.getNewVersion)
1.  [function <span class="apidocSignatureSpan">np.version.</span>isPrereleaseVersion (version)](#apidoc.element.np.version.isPrereleaseVersion)
1.  [function <span class="apidocSignatureSpan">np.version.</span>isValidVersionInput (input)](#apidoc.element.np.version.isValidVersionInput)
1.  [function <span class="apidocSignatureSpan">np.version.</span>isVersionGreater (oldVersion, newVersion)](#apidoc.element.np.version.isVersionGreater)
1.  [function <span class="apidocSignatureSpan">np.version.</span>isVersionLower (oldVersion, newVersion)](#apidoc.element.np.version.isVersionLower)
1.  [function <span class="apidocSignatureSpan">np.version.</span>satisfies (version, range)](#apidoc.element.np.version.satisfies)
1.  object <span class="apidocSignatureSpan">np.version.</span>PRERELEASE_VERSIONS
1.  object <span class="apidocSignatureSpan">np.version.</span>SEMVER_INCREMENTS



# <a name="apidoc.module.np"></a>[module np](#apidoc.module.np)



# <a name="apidoc.module.np.util"></a>[module np.util](#apidoc.module.np.util)

#### <a name="apidoc.element.np.util.readPkg"></a>[function <span class="apidocSignatureSpan">np.util.</span>readPkg ()](#apidoc.element.np.util.readPkg)
- description and source-code
```javascript
() => {
	const pkg = readPkgUp.sync().pkg;

	if (!pkg) {
		throw new Error('No package.json found. Make sure you're in the correct project.');
	}

	return pkg;
}
```
- example usage
```shell
...
	if (opts.skipCleanup) {
		opts.cleanup = false;
	}

	const runTests = !opts.yolo;
	const runCleanup = opts.cleanup && !opts.yolo;
	const runPublish = opts.publish;
	const pkg = util.readPkg();

	const tasks = new Listr([
		{
			title: 'Prerequisite check',
			task: () => prerequisiteTasks(input, pkg, opts)
		},
		{
...
```



# <a name="apidoc.module.np.version"></a>[module np.version](#apidoc.module.np.version)

#### <a name="apidoc.element.np.version.getNewVersion"></a>[function <span class="apidocSignatureSpan">np.version.</span>getNewVersion (oldVersion, input)](#apidoc.element.np.version.getNewVersion)
- description and source-code
```javascript
(oldVersion, input) => {
	if (!exports.isValidVersionInput(input)) {
		throw new Error('Version should be either ${exports.SEMVER_INCREMENTS.join(', ')} or a valid semver version.');
	}

	return exports.SEMVER_INCREMENTS.indexOf(input) === -1 ? input : semver.inc(oldVersion, input);
}
```
- example usage
```shell
...
		{
			title: 'Validate version',
			task: () => {
				if (!version.isValidVersionInput(input)) {
					throw new Error('Version should be either ${version.SEMVER_INCREMENTS.join(', ')}, or a valid semver version.');
				}

				newVersion = version.getNewVersion(pkg.version, input);

				if (!version.isVersionGreater(pkg.version, newVersion)) {
					throw new Error('New version \'${newVersion}\' should be higher than current version \'${pkg.version}\'');
				}
			}
		},
		{
...
```

#### <a name="apidoc.element.np.version.isPrereleaseVersion"></a>[function <span class="apidocSignatureSpan">np.version.</span>isPrereleaseVersion (version)](#apidoc.element.np.version.isPrereleaseVersion)
- description and source-code
```javascript
version => exports.PRERELEASE_VERSIONS.indexOf(version) !== -1 || Boolean(semver.prerelease(version))
```
- example usage
```shell
...
					throw new Error('New version \'${newVersion}\' should be higher than current version \'${pkg.version}\'');
				}
			}
		},
		{
			title: 'Check for pre-release version',
			task: () => {
				if (!pkg.private && version.isPrereleaseVersion(newVersion) && !opts.tag) {
					throw new Error('You must specify a dist-tag using --tag when publishing a pre-release version. This prevents accidentally
tagging unstable versions as "latest". https://docs.npmjs.com/cli/dist-tag');
				}
			}
		},
		{
			title: 'Check npm version',
			skip: () => version.isVersionLower('6.0.0', process.version),
...
```

#### <a name="apidoc.element.np.version.isValidVersionInput"></a>[function <span class="apidocSignatureSpan">np.version.</span>isValidVersionInput (input)](#apidoc.element.np.version.isValidVersionInput)
- description and source-code
```javascript
input => exports.SEMVER_INCREMENTS.indexOf(input) !== -1 || isValidVersion(input)
```
- example usage
```shell
...
module.exports = (input, pkg, opts) => {
	let newVersion = null;

	const tasks = [
		{
			title: 'Validate version',
			task: () => {
				if (!version.isValidVersionInput(input)) {
					throw new Error('Version should be either ${version.SEMVER_INCREMENTS.join(', ')}, or a valid semver version.');
				}

				newVersion = version.getNewVersion(pkg.version, input);

				if (!version.isVersionGreater(pkg.version, newVersion)) {
					throw new Error('New version \'${newVersion}\' should be higher than current version \'${pkg.version}\'');
...
```

#### <a name="apidoc.element.np.version.isVersionGreater"></a>[function <span class="apidocSignatureSpan">np.version.</span>isVersionGreater (oldVersion, newVersion)](#apidoc.element.np.version.isVersionGreater)
- description and source-code
```javascript
(oldVersion, newVersion) => {
	if (!isValidVersion(newVersion)) {
		throw new Error('Version should be a valid semver version.');
	}

	return semver.gt(newVersion, oldVersion);
}
```
- example usage
```shell
...
			task: () => {
				if (!version.isValidVersionInput(input)) {
					throw new Error('Version should be either ${version.SEMVER_INCREMENTS.join(', ')}, or a valid semver version.');
				}

				newVersion = version.getNewVersion(pkg.version, input);

				if (!version.isVersionGreater(pkg.version, newVersion)) {
					throw new Error('New version \'${newVersion}\' should be higher than current version \'${pkg.version}\'');
				}
			}
		},
		{
			title: 'Check for pre-release version',
			task: () => {
...
```

#### <a name="apidoc.element.np.version.isVersionLower"></a>[function <span class="apidocSignatureSpan">np.version.</span>isVersionLower (oldVersion, newVersion)](#apidoc.element.np.version.isVersionLower)
- description and source-code
```javascript
(oldVersion, newVersion) => {
	if (!isValidVersion(newVersion)) {
		throw new Error('Version should be a valid semver version.');
	}

	return semver.lt(newVersion, oldVersion);
}
```
- example usage
```shell
...
				if (!pkg.private && version.isPrereleaseVersion(newVersion) && !opts.tag) {
					throw new Error('You must specify a dist-tag using --tag when publishing a pre-release version. This prevents accidentally
tagging unstable versions as "latest". https://docs.npmjs.com/cli/dist-tag');
				}
			}
		},
		{
			title: 'Check npm version',
			skip: () => version.isVersionLower('6.0.0', process.version),
			task: () => execa.stdout('npm', ['version', '--json']).then(json => {
				const versions = JSON.parse(json);
				if (!version.satisfies(versions.npm, '>=2.15.8 <3.0.0 || >=3.10.1')) {
					throw new Error('npm@${versions.npm} has known issues publishing when running Node.js 6. Please upgrade npm or downgrade Node
 and publish again. https://github.com/npm/npm/issues/5082');
				}
			})
		},
...
```

#### <a name="apidoc.element.np.version.satisfies"></a>[function <span class="apidocSignatureSpan">np.version.</span>satisfies (version, range)](#apidoc.element.np.version.satisfies)
- description and source-code
```javascript
(version, range) => semver.satisfies(version, range)
```
- example usage
```shell
...
			}
		},
		{
			title: 'Check npm version',
			skip: () => version.isVersionLower('6.0.0', process.version),
			task: () => execa.stdout('npm', ['version', '--json']).then(json => {
				const versions = JSON.parse(json);
				if (!version.satisfies(versions.npm, '>=2.15.8 <3.0.0 || >=3.10.1')) {
					throw new Error('npm@${versions.npm} has known issues publishing when running Node.js 6. Please upgrade npm or downgrade Node
 and publish again. https://github.com/npm/npm/issues/5082');
				}
			})
		},
		{
			title: 'Check yarn.lock integrity',
			enabled: () => opts.yarn,
...
```



# misc
- this document was created with [utility2](https://github.com/kaizhu256/node-utility2)
