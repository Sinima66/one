# one
$ npx markdown-toc README.md
- [my-project](#my-project)
- [Getting started](#getting-started)
- [Usage](#usage)
  * [Example](#example)
- [API](#api)
  * [The `` element](#the--element)
    + [Attributes/Properties](#attributesproperties)
    + [Methods](#methods)
    + [Events](#events)
- [More Examples](#more-examples)
  * [Usage with [`@lume/element`](https://github.com/lume/element)](#usage-with-lumeelementhttpsgithubcomlumeelement)
  * [Usage with React](#usage-with-react)
  * [Usage with React and TypeScript](#usage-with-react-and-typescript)
  * [Usage with other view libs/frameworks](#usage-with-other-view-libsframeworks)
- [Development](#development)
  * [Test it in the examples](#test-it-in-the-examples)
  * [Test it in another project](#test-it-in-another-project)
use strict';
/*!
 * markdown-toc <https://github.com/jonschlinkert/markdown-toc>
 *
 * Copyright © 2013-2017, Jon Schlinkert.
 * Released under the MIT License.
 */
var utils = require('./lib/utils');
var querystring = require('querystring');
/**
 * expose `toc`
 */
module.exports = toc;
/**
 * Load `generate` as a remarkable plugin and
 * expose the `toc` function.
 *
 * @param  {String} `str` String of markdown
 * @param  {Object} `options`
 * @return {String} Markdown-formatted table of contents
 */
function toc(str, options) {
  return new utils.Remarkable()
    .use(generate(options))
    .render(str);
}
/**
 * Expose `insert` method
 */
toc.insert = require('./lib/insert');
/**
 * Generate a markdown table of contents. This is the
 * function that does all of the main work with Remarkable.
 *
 * @param {Object} `options`
 * @return {String}
 */
function generate(options) {
  var opts = utils.merge({firsth1: true, maxdepth: 6}, options);
  var stripFirst = opts.firsth1 === false;
  if (typeof opts.linkify === 'undefined') opts.linkify = true;
  return function(md) {
    md.renderer.render = function(tokens) {
      tokens = tokens.slice();
      var seen = {};
      var len = tokens.length, i = 0, num = 0;
      var tocstart = -1;
      var arr = [];
      var res = {};
      while (len--) {
        var token = tokens[i++];
        if (/<!--[ \t]*toc[ \t]*-->/.test(token.content)) {
          tocstart = token.lines[1];
        }
        if (token.type === 'heading_open') {
          tokens[i].lvl = tokens[i - 1].hLevel;
          tokens[i].i = num++;
          arr.push(tokens[i]);
        }
      }
      var result = [];
      res.json = [];







use strict';
/*!
 * markdown-toc <https://github.com/jonschlinkert/markdown-toc>
 *
 * Copyright © 2013-2017, Jon Schlinkert.
 * Released under the MIT License.
 */
var utils = require('./lib/utils');
var querystring = require('querystring');
/**
 * expose `toc`
 */
module.exports = toc;
/**
 * Load `generate` as a remarkable plugin and
 * expose the `toc` function.
 *
 * @param  {String} `str` String of markdown
 * @param  {Object} `options`
 * @return {String} Markdown-formatted table of contents
 */
function toc(str, options) {
  return new utils.Remarkable()
    .use(generate(options))
    .render(str);
}
/**
 * Expose `insert` method
 */
toc.insert = require('./lib/insert');
/**
 * Generate a markdown table of contents. This is the
 * function that does all of the main work with Remarkable.
 *
 * @param {Object} `options`
 * @return {String}
 */
function generate(options) {
  var opts = utils.merge({firsth1: true, maxdepth: 6}, options);
  var stripFirst = opts.firsth1 === false;
  if (typeof opts.linkify === 'undefined') opts.linkify = true;
  return function(md) {
    md.renderer.render = function(tokens) {
      tokens = tokens.slice();
      var seen = {};
      var len = tokens.length, i = 0, num = 0;
      var tocstart = -1;
      var arr = [];
      var res = {};
      while (len--) {
        var token = tokens[i++];
        if (/<!--[ \t]*toc[ \t]*-->/.test(token.content)) {
          tocstart = token.lines[1];
        }
        if (token.type === 'heading_open') {
          tokens[i].lvl = tokens[i - 1].hLevel;
          tokens[i].i = num++;
          arr.push(tokens[i]);
        }
      }
      var result = [];
      res.json = [];
Ya 

