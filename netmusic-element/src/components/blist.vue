<template>
  <div class="maxl">
    <div class="bboxl">
      <span class="circle"></span>
      <span class="start">榜单</span>
      <span class="arrow">更多</span>
    </div>
    <div class="list">
      <el-table
        header-cell-class-name="tableStyle"
        :data="top"
        :row-class-name="tableRowClassName"
        cell-class-name="cellclass"
        style="width: 100%"
      >
        <el-table-column type="index" width="45">
          <template slot="header" slot-scope="scope">
            <button class="diyimg"><span class="cover"></span></button>
          </template>
        </el-table-column>
        <el-table-column width="197">
          <template slot="header" slot-scope="scope">
            <button class="diytext"><h3>飙升榜</h3></button>
          </template>
          <el-table-column show-overflow-tooltip prop="name" width="100">
            <template slot="header" slot-scope="scope">
              <a href="#"> <i class="icon-video-play"></i></a>
            </template>
          </el-table-column>
          <el-table-column width="97">
            <template slot-scope="scope">
              <el-button
                class="u-btn"
                size="mini"
                type="text"
                icon="icon-play"
              ></el-button>
              <el-button class="u-btn" size="mini" type="text" icon="el-plus"></el-button>
              <el-button
                class="u-btn"
                size="mini"
                type="text"
                icon="icon-add"
              ></el-button>
            </template>
          </el-table-column>
        </el-table-column>
      </el-table>

      <el-table
        header-cell-class-name="tableStyle"
        :data="newsong"
        :row-class-name="tableRowClassName"
        cell-class-name="cellclass"
        style="width: 100%"
      >
        <el-table-column type="index" width="45">
          <template slot="header" slot-scope="scope">
            <button class="diyimg2"><span class="cover"></span></button>
          </template>
        </el-table-column>
        <el-table-column width="197">
          <template slot="header" slot-scope="scope">
            <button class="diytext"><h3>新歌榜</h3></button>
          </template>
          <el-table-column prop="name" show-overflow-tooltip width="100">
            <template slot="header" slot-scope="scope">
              <a href="#"> <i class="icon-video-play"></i></a>
            </template>
          </el-table-column>
          <el-table-column width="97">
            <template slot-scope="scope">
              <el-button
                class="u-btn"
                size="mini"
                type="text"
                icon="icon-play"
              ></el-button>
              <el-button class="u-btn" size="mini" type="text" icon="el-plus"></el-button>
              <el-button
                class="u-btn"
                size="mini"
                type="text"
                icon="icon-add"
              ></el-button>
            </template>
          </el-table-column>
        </el-table-column>
      </el-table>

      <el-table
        header-cell-class-name="tableStyle"
        :data="ori"
        :row-class-name="tableRowClassName"
        cell-class-name="cellclass"
        style="width: 100%"
      >
        <el-table-column type="index" width="45">
          <template slot="header" slot-scope="scope">
            <button class="diyimg3"><span class="cover"></span></button>
          </template>
        </el-table-column>
        <el-table-column width="196">
          <template slot="header" slot-scope="scope">
            <button class="diytext"><h3>原创榜</h3></button>
          </template>
          <el-table-column prop="name" show-overflow-tooltip width="100">
            <template slot="header" slot-scope="scope">
              <a href="#"> <i class="icon-video-play"></i></a>
            </template>
          </el-table-column>
          <el-table-column width="96">
            <template slot-scope="scope">
              <el-button
                class="u-btn"
                size="mini"
                type="text"
                icon="icon-play"
              ></el-button>
              <el-button class="u-btn" size="mini" type="text" icon="el-plus"></el-button>
              <el-button
                class="u-btn"
                size="mini"
                type="text"
                icon="icon-add"
              ></el-button>
            </template>
          </el-table-column>
        </el-table-column>
      </el-table>

      <el-row>
        <el-col :span="8"
          ><div class="bbr"><a href="#">查看全部></a></div></el-col
        >
        <el-col :span="8"
          ><div><a href="#">查看全部></a></div></el-col
        >
        <el-col :span="8"
          ><div class="bbl"><a href="#">查看全部></a></div></el-col
        >
      </el-row>
    </div>
  </div>
</template>
<script>
import axios from "../plugins/axios.js";
export default {
  data() {
    return {
      top: [{ name: "" }],
      newsong: [{ name: "" }],
      ori: [{ name: "" }],
      showIcon: false,
    };
  },
  created() {
    this.gettop();
    this.getnew();
    this.getori();
  },
  methods: {
    tableRowClassName({ row, rowIndex }) {
      if (rowIndex % 2 == 0) {
        return "warning-row";
      } else if (rowIndex % 2 !== 0) {
        return "success-row";
      }
      return "";
    },

    gettop() {
      axios({
        url: "playlist/detail?id=19723756",
        methods: "get",
      })
        .then((res) => {
          //  console.log(res);
          let arrtop = res.data.playlist.tracks;
          this.top = arrtop.slice(0, 10);
        })
        .catch((error) => {
          console.log(error);
        });
    },
    getnew() {
      axios({
        url: "playlist/detail?id=3779629",
        methods: "get",
      })
        .then((res) => {
          //  console.log(res);
          let arrnew = res.data.playlist.tracks;
          this.newsong = arrnew.slice(0, 10);
        })
        .catch((error) => {
          console.log(error);
        });
    },
    getori() {
      axios({
        url: "playlist/detail?id=2884035",
        methods: "get",
      })
        .then((res) => {
          // console.log(res);
          let arrori = res.data.playlist.tracks;
          this.ori = arrori.slice(0, 10);
        })
        .catch((error) => {
          console.log(error);
        });
    },
  },
};
</script>
<style lang="scss">
.maxl {
  margin-top: 20px;
  height: 600px;
  overflow: hidden;
  .bboxl {
    width: 100%;
    height: 35px;
    line-height: 35px;
    text-align: left;
    border-bottom: 2px solid #c10d0c;
    font-size: 12px;
    color: #666;
    .circle {
      display: inline-block;
      margin-right: 10px;
      width: 20px;
      height: 20px;
      background: url("../assets/image/index.png");
      background-position: 183px 305px;
    }
    .arrow {
      display: inline-block;
      margin-left: 580px;
      width: 35px;
      height: 20px;
      background: url("../assets/image/index.png");
      background-position: 25px 700px;
    }
    .start {
      line-height: 35px;
      font-size: 20px;
      color: #333;
      margin-right: 25px;
    }
    .list {
    }
  }

  .list {
    margin-top: 20px;
    display: flex;
    flex-direction: row;
    flex-wrap: wrap;
    border: 1px solid #d3d3d3;
    .el-table_2_column_6_column_7:hover {
      text-decoration: underline;
      cursor: point;
    }
    .el-table_3_column_10_column_11:hover {
      text-decoration: underline;
      cursor: point;
    }
    .el-table_1_column_2_column_3:hover {
      text-decoration: underline;
      cursor: pointer;
    }

    .el-table tbody tr:hover > td {
      padding: 0px !important;
      background-color: transparent;
      cursor: pointer;
    }

    .el-table__body.tr {
      height: 23px;
    }

    .el-table__header-wrapper {
      overflow: hidden;
      padding: 10px;
      background-color: #f4f4f4;
      padding-top: 18px;
      width: 220px;
    }
    .el-table thead.is-group th {
      background: #f4f4f4;
    }
    .el-table__header {
      table-layout: auto;
    }
    .el-table th {
      padding: 0px;
    }
    .tableStyle {
      border: none;

      .cell {
        .diyimg {
          border: none;
          width: 80px;
          height: 80px;
          padding-left: 0px;
          background: url("../assets/image/biao.jpg");
          background-position: -10px -10px;
          .cover {
            background: url("../assets/image/coverall.png");
            background-position: -145px -57px;
            display: block;
            width: 80px;
            height: 80px;
          }
        }
        .diyimg2 {
          border: none;
          width: 80px;
          height: 80px;
          padding-left: 0px;
          background: url("../assets/image/new.jpg");
          background-position: -10px -10px;
          .cover {
            background: url("../assets/image/coverall.png");
            background-position: -145px -57px;
            display: block;
            width: 80px;
            height: 80px;
          }
        }
        .diyimg3 {
          border: none;
          width: 80px;
          height: 80px;
          padding-left: 0px;
          background: url("../assets/image/ori.jpg");
          background-position: -10px -10px;
          .cover {
            background: url("../assets/image/coverall.png");
            background-position: -145px -57px;
            display: block;
            width: 80px;
            height: 80px;
          }
        }

        .diytext {
          border: none;
          background-color: inherit;

          h3 {
            font-size: 14px;
          }
          h3:hover {
            text-decoration: underline;
            cursor: pointer;
          }
        }
        .icon-video-play {
          background: url("../assets/image/index.png");
          background-position: 146px 260px;
          display: block;
          width: 60px;
          height: 22px;
        }
      }
    }

    .el-row {
      width: 100%;
      height: 32px;
      background-color: #e8e8e8;
      div {
        font-size: 12px;
        text-align: right;
        line-height: 32px;
        a {
          display: inline-block;
          margin-right: 30px;
          text-decoration: none;
          color: #000;
        }
        a:hover {
          text-decoration: underline;
          cursor: pointer;
        }
      }
      .bbr {
        border-right: 1px solid #d3d3d3;
      }
      .bbl {
        border-left: 1px solid #d3d3d3;
      }
    }
    .u-btn {
      display: none;
    }
    .el-table__body tr:hover {
      .u-btn {
        display: inline;
      }
    }
    // border:1px  solid #d3d3d3;
    .el-table:nth-child(3) {
      border-right: none;
    }
    .el-table {
      border-right: 1px solid #d3d3d3;
      border-bottom: none;
      color: #000;
      font-size: 12px;

      .cellclass {
        padding-top: 5px;
        padding-bottom: 5px;
        .icon-play {
          background: url("../assets/image/index.png");
          background-position: 146px 197px;
          display: block;
          width: 17px;
          height: 17px;
        }
        .icon-add {
          background: url("../assets/image/index.png");
          background-position: 116px 197px;
          display: block;
          width: 17px;
          height: 17px;
        }
        .el-plus {
          background: url("../assets/image/icon.png");
          background-position: 65px 408px;
          display: block;
          width: 17px;
          height: 17px;
        }
      }
      .cell {
        // height: 23px;
        padding-left: 5px;
        padding-right: 5px;
        div {
          font-size: 16px;
          color: #666;
          text-align: right;
        }
      }
      .warning-row {
        background: #e8e8e8;
      }
      .success-row {
        background: #f4f4f4;
      }
    }
  }
}
</style>
